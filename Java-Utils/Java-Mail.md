# Java Mail 1.6.2

API JavaMail cung cấp một giao thức độc lập để xây dựng các ứng dụng làm việc với email. API JavaMail có sẵn dưới dạng gói tùy chọn để sử dụng với nền tảng Java SE và nền tảng Java EE .

#### Latest News [August 29, 2018 - JavaMail 1.6.2 Final Release](https://github.com/javaee/javamail/releases)

### Download JavaMail Release
Bản phát hành mới nhất của JavaMail là 1.6.2.

|Item|Description|
|---|---|
|[javax.mail.jar](https://github.com/javaee/javamail/releases/download/JAVAMAIL-1_6_2/javax.mail.jar)|The JavaMail reference implementation, including the SMTP, IMAP, and POP3 protocol providers|

### Code example

```java

import javax.mail.*;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import java.util.Properties;

/**
 *
 * @author anhdt
 */
public class JavaMailDemo {
    
    private final String MAIL = " ";
    private final String PASSWORD = "******";
    
    public void sentEmail(String toEmail, String subject, String text) {
        
        // Config
        Properties props = new Properties();
        props.put("mail.smtp.auth", "true");
        props.put("mail.smtp.starttls.enable", "true");
        props.put("mail.smtp.host", "smtp.gmail.com");
        
        // Authenticator
        Session session = Session.getInstance(props, new Authenticator() {
            @Override
            protected PasswordAuthentication getPasswordAuthentication() {
                return new PasswordAuthentication(MAIL, PASSWORD);
            }
        });

        // Mail info
        try {
            Message message = new MimeMessage(session);
            message.setFrom(new InternetAddress(MAIL));
            message.setRecipients(Message.RecipientType.TO, InternetAddress.parse(toEmail));
            message.setSubject(subject);
            message.setText(text);

            Transport.send(message);           
            System.out.println("Sent email done!");
            
        } catch (MessagingException e) {
            throw new RuntimeException(e);
        }
    }    
}

```
