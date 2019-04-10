# Beego

dfsssssss

![](/assets/111.png)






```java

			
			if(null != params && params.size() > 0) {
				for (Variable variable : params) {
					context.setVariable(variable.getName(), variable.getValue());
				}
			}
			text = templateEngine.process(mail.getTemplateName(), context);
			
			
		}

		MimeMessage mimeMessage = javaMailSender.createMimeMessage();
		MimeMessageHelper mimeMessageHelper = new MimeMessageHelper(mimeMessage, true, "utf-8");
		mimeMessageHelper.setTo(mail.getTo());
		mimeMessageHelper.setSubject(mail.getSubject());
		mimeMessageHelper.setFrom(from);
		mimeMessageHelper.setText(text, true);
		String[] cc = mail.getCc();
		if(null != cc && cc.length > 0) {
			mimeMessageHelper.setCc(cc);

```