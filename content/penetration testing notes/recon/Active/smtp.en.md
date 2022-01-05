---
  title: "SMTP"
---
# intro
# background
#### SMTP Commands
- ATRN 	This command performs the TURN operation (reversal of roles of email client and server) only if the connection is authenticated.
CHUNKING 	This is an ESMTP command, whose function is similar to DATA (a message sent by the client to the server to start the process of sending the email), except that the mechanism used by the server to figure out where the message ends is different; the number of bytes in the message is explicitly sent, and the server counts the number of bytes it has received.
- DATA 	This command gives the server an intimation that it is ready to begin sending the email.
- DSN 	This command activates the reception of delivery status notifications of the email message.
- EHLO 	An email client that supports ESMTP sends this command, and the server returns a list of ESMTPcommands that it supports. The syntax of this command requires the sender to provide his or her own domain name as a parameter.
- ETRN 	This command is sent by an email server to another server, requesting it to start sending email messages located on it.
- HELP 	This command is used to ask for help from the email server, and it requests the server to return a list of commands it supports.
- HELO 	To begin an SMTP session between the sender and the server, and also so as to enable the server to be able to identify the sender, this command is sent. The syntax of this command requires the sender to send his or her domain name as a parameter.
- MAIL FROM: 	To begin the process of composing the email, and to allow the server to know the sender’s identity, this command is used, and its syntax requires it to compulsorily take the sender’s email address as a parameter, along with other optional parameters.
- NOOP 	This command performs no operation, and is used solely to verify the connectivity with the server.
-PIPELINING 	On a terminal or command prompt, response packets for every action performed are immediately visible to the sender. This command turns on pipelining, which allows one to send more than one command at a time before receiving responses.
- QUIT 	This command is used to terminate the SMTPsession.
- RCPT TO: 	The syntax of this command requires the recipient’s email address to be provided as a compulsory parameter, in addition to other optional ones. It is used to specify the recipient of the email message.
- RSET 	This command is used to perform a reset action; the current conversation is terminated, or message being composed discarded, and one can start again.
- SAML 	This command asks the server to send the message to the recipient’s email client, as well as directly to the recipient’s terminal.
- SEND 	This command is used to send email messages directly to the recipient’s terminal, instead of sending it to his or her email client.
- SIZE= 	This command is used to specify the size of the message being sent, in terms of number of bytes. It comes into use when the server has set a limitation on the size of incoming email messages. In the absence of this explicit declaration of the size of the message, the server tries to determine the same by using other methods.
- SOML 	This command sends emails directly to the recipient’s terminal if he or she is online. Otherwise, the message is sent to the recipient’s email client.
- TURN 	This command is used to invert the functionality of the email client, and the email server. The client can receive messages from the server while using the same connection.
- VRFY 	In the syntax of this command, the recipient’s email address is taken as a parameter. This command requests the email server to verify the authenticity, or existence, of the remote user from the email address.
- EXPN This SMTP command asks for a confirmation about the identification of a mailing list.

VRFY, EXPN and RCPT can be used to identify users.
e.g., VRFY root

# techniques
# resources

nc


Port enumeration
`nmap -script smtp-commands.nse 192.168.1.101`


enumerate users
smtp-user-enum
`smtp-user-enum -M VRFY -U /root/sectools/SecLists/Usernames/Names/names.txt -t 192.168.1.103`

metasploit
`msf > use auxiliary/scanner/smtp/smtp_enum `
