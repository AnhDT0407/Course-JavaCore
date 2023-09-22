# Java Mail 1.6.2

API JavaMail cung cấp một giao thức độc lập để xây dựng các ứng dụng làm việc với email. API JavaMail có sẵn dưới dạng gói tùy chọn để sử dụng với nền tảng Java SE và nền tảng Java EE .

### 1. Download JavaMail Release

|Maven|
|---|
|[https://mvnrepository.com/artifact/com.sun.mail/jakarta.mail/2.0.1](https://mvnrepository.com/artifact/com.sun.mail/jakarta.mail/2.0.1)|

### 2. Code example

Ví dụ này là một ví dụ dùng **Gmail** để gửi đi một emai đơn giản.

```java
        
import jakarta.mail.*;
import jakarta.mail.internet.InternetAddress;
import jakarta.mail.internet.MimeMessage;
import java.util.Properties;

/**
 *
 * @author anhdt
 */
public class JavaMailDemo {
    
    private final String MAIL = "";      // email from
    private final String PASSWORD = "";  // password for authentication
    
    public void sentEmail(String toEmail, String subject, String text) {
        
        // Config
        Properties props = new Properties();
        props.put("mail.smtp.auth", "true");
        props.put("mail.smtp.starttls.enable", "true");
        props.put("mail.smtp.host", "smtp.gmail.com");
        props.put("mail.smtp.port", "587");
        
        // Authenticator
        Session session = Session.getInstance(props,
            new jakarta.mail.Authenticator() {
                protected PasswordAuthentication getPasswordAuthentication() {
                    return new PasswordAuthentication(IConstant.MAIL, IConstant.PASSWORD);
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
            System.out.println("Message sent successfully...");
            
        } catch (MessagingException e) {
            throw new RuntimeException(e);
        }
    }    
}

```

Chạy ví dụ với hàm `main`
```java
/**
 * @param args the command line arguments
 */
public static void main(String[] args) {
    String toEmail = "";
    String subject = "[JavaMail] - Demo sent email";
    String text = "Thank you for using JavaMail";
    new JavaMailDemo().sentEmail(toEmail, subject, text);
}
```

Output
```java
run:
Message sent successfully...
BUILD SUCCESSFUL (total time: 5 seconds)
```
<br />

### 3. Lấy mật khẩu gửi email

#### 3.1. Truy cập link [https://myaccount.google.com/security](https://myaccount.google.com/security)

#### 3.2. Bật xác thực 2 bước (2-Step Verification) và click vào `2-Step Verification`

<br />

<p align="center">
  <img src="https://github.com/AnhDT0407/Course-JavaCore/blob/master/Java-Utils/IMG/2023-09-22_230658.png">
</p>

<br />


