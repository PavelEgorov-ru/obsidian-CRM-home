**Пример отчета MTA (bounce email) с hard bounce:**  
```
Subject: Delivery Status Notification (Failure)
From: Mail Delivery System <Mailer-Daemon@example.net>
To: sender@example.com
This is an automatically generated Delivery Status Notification.
Delivery to the following recipient failed permanently:
 recipient@nonexistentdomain.com
Reason: Permanent Error: 550 5.1.1 <recipient@nonexistentdomain.com>: Recipient address rejected: Domain not found
Final-Recipient: RFC822; recipient@nonexistentdomain.com
Action: failed
Status: 5.1.1
Diagnostic-Code: smtp; 550 5.1.1 <recipient@nonexistentdomain.com>: Recipient address rejected: Domain not found
```

  
**Как читать отчет MTA с hard bounce:**    
• `Subject: Delivery Status Notification (Failure)`**:** Тема письма ясно указывает на неудачную доставку.    
• `From: Mail Delivery System <Mailer-Daemon@example.net>`**:** Отправитель - это системный адрес почтового сервера.    
• `Reason: Permanent Error: 550 5.1.1 ...`**:** Указывает на постоянную ошибку. Код ошибки `550 5.1.1` и сообщение `Domain not found` означают, что домен получателя не существует.  
• `Final-Recipient: RFC822; recipient@nonexistentdomain.com`**:** Адрес получателя, которому не удалось доставить письмо.    
• `Status: 5.1.1`**:** SMTP код статуса ошибки.  
  
  
**Пример отчета MTA (bounce email) с soft bounce:**  
```
Subject: Delivery Status Notification (Delay)
From: Mail Delivery System <Mailer-Daemon@example.net>
To: sender@example.com
This is an automatically generated Delivery Status Notification.
Message delayed: connection timed out with example.org[192.0.2.4].
Will keep trying until message expires.
Final-Recipient: RFC822; recipient@example.org
Action: delayed
Status: 4.4.7
Diagnostic-Code: smtp; 451 4.4.7 Timeout waiting for client input
```
  
**Как читать отчет MTA с soft bounce:**    
• `Subject: Delivery Status Notification (Delay)`**:** Тема указывает на задержку доставки.   
• `Message delayed: connection timed out ...`**:** Причина задержки - тайм-аут соединения с сервером получателя.    
• `Will keep trying until message expires.`**:** MTA будет пытаться доставить письмо повторно.    
• `Status: 4.4.7`**:** SMTP код статуса, указывающий на временную ошибку.  
  
  
**Наиболее распространенные коды SMTP**
**2xx (Успех):**    
• **`250 OK`:** Самый желаемый ответ. Сообщение успешно принято для доставки.    
• **`251 User not local; will forward to <forward-path>`:** Сервер принял сообщение, но пользователь не существует на этом сервере. Сообщение будет перенаправлено.  
  
**3xx (Дополнительная информация):** Эти коды встречаются реже.  
• **`354 Start mail input; end with <CRLF>.<CRLF>`:** Сервер готов принять тело письма после этой команды.  
  
**4xx (Временная ошибка):** Эти ошибки могут быть временными. Попробуйте отправить письмо позже.    
• **`421 <domain> Service not available, closing transmission channel`:** Сервер временно недоступен. Это может быть связано с перегрузкой сервера или техническим обслуживанием.    
• **`450 Requested mail action not taken: mailbox unavailable`:** Почтовый ящик получателя временно недоступен. Это может быть связано с переполненным ящиком или временной блокировкой.    
• **`451 Requested action aborted: local error in processing`:** На сервере произошла ошибка. Попробуйте позже.    
• **`452 Requested action not taken: insufficient system storage`:** На сервере недостаточно места для хранения сообщения.    
• **`455 Server unable to accommodate parameters`:** Сервер не может обработать параметры команды.  
  
**5xx (Постоянная ошибка):** Эти ошибки указывают на серьезную проблему, требующую вмешательства.   
• **`500 Syntax error, command unrecognized`:** Синтаксическая ошибка в команде.   
• **`501 Syntax error in parameters or arguments`:** Синтаксическая ошибка в параметрах команды.    
• **`502 Command not implemented`:** Команда не поддерживается сервером.  
• **`503 Bad sequence of commands`:** Неправильная последовательность команд.   
• **`504 Command parameter not implemented`:** Параметр команды не поддерживается.  
• **`521 <domain> does not accept mail (see RFC1846)`:** Сервер не принимает почту для этого домена. Это может быть связано с политикой сервера или проблемами с DNS.  
• **`550 Requested action not taken: mailbox unavailable`:** Почтовый ящик получателя не существует или недоступен. Это наиболее распространенная причина постоянной ошибки. Проверьте адрес получателя.  
• **`551 User not local; please try <forward-path>`:** Пользователь не существует на этом сервере, но сервер предлагает альтернативный адрес для пересылки.  
• **`552 Requested mail action aborted: exceeded storage allocation`:** Почтовый ящик получателя переполнен.  
• **`553 Requested action not taken: mailbox name not allowed`:** Имя почтового ящика недопустимо. 
• **`554 Transaction failed`:** Транзакция не удалась по неизвестной причине.