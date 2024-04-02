import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

# Email account credentials
sender_email = "jideejiwole@gmail.com"
sender_password = "Hollarjay0823$"

# Recipients
recipients = ["recipient1@example.com", "recipient2@example.com"]

# Create the email message
message = MIMEMultipart()
message["From"] = sender_email
message["To"] = ", ".join(recipients)
message["Subject"] = "Test Email"

body = "This is a test email sent from Python."
message.attach(MIMEText(body, "plain"))

# Connect to the SMTP server
with smtplib.SMTP("smtp.gmail.com", 587) as server:
    server.starttls()  # Enable TLS encryption
    server.login(sender_email, sender_password)  # Login to the email account
    server.sendmail(sender_email, recipients, message.as_string())  # Send the email
