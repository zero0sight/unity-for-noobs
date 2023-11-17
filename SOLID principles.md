# SOLID principles in C#

Solid design principles in c# are basic design principles.

Solid stands for:
- Single resposibilty principle (SRP)
- Open closed principle (OCP)
- Liskov substitution principle (LSP)
- Interface segregation principle (ISP)
- Dependency inversion principle (DIP)

## Single responsibility principle (SRP)
The Single Responsibility Principle is often defined as: An object should only have one reason to change.

the longer the file or class, the more difficult it will be to achieve this. With that definition in mind, look at this code:
```C#
public class UserService
{
   public void Register(string email, string password)
   {
      if (!ValidateEmail(email))
         throw new ValidationException("Email is not an email");
         var user = new User(email, password);

         SendEmail(new MailMessage("mysite@nowhere.com", email) { Subject="HEllo foo" });
   }
   public virtual bool ValidateEmail(string email)
   {
     return email.Contains("@");
   }
   public bool SendEmail(MailMessage message)
   {
     _smtpClient.Send(message);
   }
}
```
It looks fine, but it is not following SRP.

The SendEmail and ValidateEmail methods have nothing to do with the UserService class. Let's refract it.
```C#
public class UserService
{
   EmailService _emailService;
   DbContext _dbContext;
   public UserService(EmailService aEmailService, DbContext aDbContext)
   {
      _emailService = aEmailService;
      _dbContext = aDbContext;
   }
   public void Register(string email, string password)
   {
      if (!_emailService.ValidateEmail(email))
         throw new ValidationException("Email is not an email");
         var user = new User(email, password);
         _dbContext.Save(user);
         emailService.SendEmail(new MailMessage("myname@mydomain.com", email) {Subject="Hi. How are you!"});

      }
   }
   public class EmailService
   {
      SmtpClient _smtpClient;
   public EmailService(SmtpClient aSmtpClient)
   {
      _smtpClient = aSmtpClient;
   }
   public bool virtual ValidateEmail(string email)
   {
      return email.Contains("@");
   }
   public bool SendEmail(MailMessage message)
   {
      _smtpClient.Send(message);
   }
}
```
