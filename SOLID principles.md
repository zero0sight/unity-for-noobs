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
// Bad example
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

## Open/Closed principle (OCP)
That brings us to the next principle: open for extension, closed for modification.

How is it done? Preferably not like this:
```C#
// Bad example
void DrawNerd(Nerd nerd) {
  if (nerd.IsSelected)
    DrawEllipseAroundNerd(nerd.Position, nerd.Radius);
  if (nerd.Image != null)
    DrawImageOfNerd(nerd.Image, nerd.Position, nerd.Heading);
  if (nerd is IHasBelt) // a rare occurrence
    DrawBelt(((IHasBelt)nerd).Belt);
  // Etc.
}
```
What’s wrong here? Well, you’ll have to modify this method every time a customer needs new things displayed—and they always need new things displayed.

You need a better plan, but how? What will it look like? Well, you have some code that knows how to draw certain things. That’s fine. You just need a general procedure for matching those things with the code to draw them. It will essentially come down to a pattern like this:
```C#
readonly IList<IRenderer> _renderers = new List<IRenderer>();
void Draw(Nerd nerd)
{
  foreach (var renderer in _renderers)
    renderer.DrawIfPossible(_context, nerd);
}
```

## Liskov substitution principle (LSP)
The Liskov Substitution Principle (LSP) states, "you should be able to use any derived class instead of a parent class and have it behave in the same manner without modification".

It ensures that a derived class does not affect the behavior of the parent class; in other words, a derived class must be substitutable for its base class.

This principle is just an extension of the Open Closed Principle, and we must ensure that newly derived classes extend the base classes without changing their behavior.

## Interface segregation principle (ISP)
The Interface Segregation Principle states "that clients should not be forced to implement interfaces they don't use.

Instead of one fat interface, many small interfaces are preferred based on groups of methods, each serving one submodule".

## Dependency inversion principle (DIP)
The Dependency Inversion Principle (DIP) states that high-level modules/classes should not depend on low-level modules/classes.

First, both should depend upon abstractions.

Secondly, abstractions should not rely upon details. Finally, details should depend upon abstractions.
