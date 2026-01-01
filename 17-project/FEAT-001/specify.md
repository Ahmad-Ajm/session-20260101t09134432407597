# Specification: User Registration & Login (FEAT-001)

## Functional Requirements

1. **User Registration**
   - Users can register using email and password.
   - Users can register using Google or Facebook accounts.
   - During registration, users must select their account type:
     - Participant
     - Organizer
   - Registration form fields: Name, Email, Password, Account Type
   - Email verification is required for email-based registration.

2. **User Login**
   - Users can log in using email/password or social login.
   - Only verified users can log in.

3. **Password Reset**
   - Users can request a password reset link via email.
   - Users can set a new password using the link.

4. **Security**
   - Use JWT authentication (ABP default).
   - Passwords are hashed and never stored in plain text.
   - Rate limiting on login attempts (ABP default or custom).

5. **Localization & Responsiveness**
   - All forms and messages are fully localized in Arabic.
   - Forms are mobile responsive.

## Non-Functional Requirements

- Use ABP Identity module for user management.
- Integrate with Google and Facebook OAuth for social login.
- Email service for verification and password reset (SMTP or provider).
- C# backend, Angular frontend.

## Acceptance Criteria

- [ ] User can register and log in via email/password.
- [ ] User can register and log in via Google/Facebook.
- [ ] User must select account type during registration.
- [ ] Email verification is required for email-based registration.
- [ ] Password reset works as described.
- [ ] All forms/messages are in Arabic and mobile responsive.
- [ ] Security best practices are followed.
