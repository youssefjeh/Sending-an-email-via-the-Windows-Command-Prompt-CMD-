# Sending-an-email-via-the-Windows-Command-Prompt-CMD

Sending an email via the Windows Command Prompt (CMD) typically involves using a third-party tool or a script. Windows does not have a built-in command for sending emails directly. Below are steps to achieve this:

### Option 1: Using PowerShell
PowerShell is often used for this task instead of CMD because it has built-in cmdlets for sending emails.

#### Steps:
1. **Open PowerShell**:
   - Press `Win + R`, type `powershell`, and hit Enter.

2. **Run the following command**:
   Replace the placeholders with your actual SMTP server details, sender email, recipient email, and credentials.

   ```powershell
   Send-MailMessage -From "your_email@example.com" -To "recipient_email@example.com" -Subject "Test Email" -Body "This is a test email" -SmtpServer "smtp.example.com" -Credential (Get-Credential) -UseSsl
   ```

   - Replace `smtp.example.com` with your SMTP server address.
   - When prompted, enter your email credentials.

3. **Send Email**:
   The email should now be sent.

---

### Option 2: Using Blat (Third-party Tool)
Blat is a command-line utility for sending emails.

#### Steps:
1. **Download Blat**:
   Download Blat from its [official website](https://www.blat.net/) or a trusted source.

2. **Install Blat**:
   Extract the downloaded files and add the folder path to your system's `PATH` environment variable for easy access.

3. **Configure Blat**:
   Open CMD and configure Blat with your SMTP server details:
   ```cmd
   blat -install smtp.example.com your_email@example.com
   ```

4. **Send Email**:
   Use the following command to send an email:
   ```cmd
   blat -to recipient_email@example.com -subject "Test Email" -body "This is a test email body." -server smtp.example.com -f your_email@example.com -u your_email_username -pw your_email_password
   ```

   - Replace the placeholders with actual values.

---

### Option 3: Using Python Script from CMD
If you have Python installed, you can use it to send emails.

#### Steps:
1. **Create a Python Script**:
   Save the following code as `send_email.py`:
   ```python
   import smtplib

   server = smtplib.SMTP('smtp.example.com', 587)
   server.starttls()
   server.login('your_email@example.com', 'your_password')
   server.sendmail(
       'your_email@example.com',
       'recipient_email@example.com',
       'Subject: Test Email\n\nThis is a test email.'
   )
   server.quit()
   ```

2. **Run the Script in CMD**:
   Navigate to the directory containing `send_email.py` and run:
   ```cmd
   python send_email.py
   ```


