# Introduction

hello gitbook


## 这里是二级标题


dddddddddd


```java
MimeMessage mimeMessage = javaMailSender.createMimeMessage();
MimeMessageHelper mimeMessageHelper = new MimeMessageHelper(mimeMessage, true, "utf-8");
mimeMessageHelper.setTo(mail.getTo());
mimeMessageHelper.setSubject(mail.getSubject());
mimeMessageHelper.setFrom(from);
mimeMessageHelper.setText(text, true);
```

