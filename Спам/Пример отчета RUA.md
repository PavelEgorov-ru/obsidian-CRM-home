```
<?xml version="1.0" encoding="UTF-8" ?>
<feedback>
 <report_metadata>
 <org_name>Example.com</org_name>
 <email>dmarc_reports@example.com</email>
 <extra_contact_info>http://example.com/dmarc/</extra_contact_info>
 <report_id>1234567890</report_id>
 <date_range>
 <begin>1678886400</begin>
 <end>1679059199</end>
 </date_range>
 </report_metadata>
 <policy_published>
 <domain>example.com</domain>
 <adkim>r</adkim>
 <aspf>r</aspf>
 <p>none</p>
 <sp>none</sp>
 <pct>100</pct>
 </policy_published>
 <record>
 <row>
 <source_ip>192.0.2.1</source_ip>
 <count>100</count>
 <policy_evaluated>
 <disposition>none</disposition>
 <dkim>pass</dkim>
 <spf>pass</spf>
 </policy_evaluated>
 </row>
 <row>
 <source_ip>198.51.100.1</source_ip>
 <count>5</count>
 <policy_evaluated>
 <disposition>none</disposition>
 <dkim>fail</dkim>
 <spf>fail</spf>
 </policy_evaluated>
 </row>
 </record>
</feedback>

```

  
**Как читать отчет RUA:**  
  
1. `<report_metadata>`**:** Метаданные отчета.  
 * `<org_name>`: Название организации, отправляющей отчет.  
 * `<email>`: Адрес электронной почты отправителя отчета.  
 * `<report_id>`: Уникальный идентификатор отчета.  
 * `<date_range>`: Период, за который собран отчет. `<begin>` и `<end>` - это временные метки Unix (количество секунд с 1 января 1970 года).  
  
2. `<policy_published>`**:** Опубликованная DMARC-политика для домена.  
 * `<domain>`: Домен, для которого применяется политика.  
 * `<adkim>`: Выравнивание DKIM (`r` - relaxed, `s` - strict).  
 * `<aspf>`: Выравнивание SPF (`r` - relaxed, `s` - strict).  
 * `<p>`: Политика DMARC (`none`, `quarantine`, `reject`).  
 * `<sp>`: Политика DMARC для поддоменов (`none`, `quarantine`, `reject`).  
 * `<pct>`: Процент писем, к которым применяется политика (обычно 100).  
  
3. `<record>`**:** Содержит информацию о каждом источнике IP, отправлявшем письма от имени вашего домена.  
 * `<row>`: Информация об одном источнике IP.  
 * `<source_ip>`: IP-адрес отправителя.  
 * `<count>`: Количество писем, отправленных с этого IP-адреса.  
 * `<policy_evaluated>`: Результаты проверки DMARC.  
 * `<disposition>`: Действие, предпринятое почтовым сервером (`none`, `quarantine`, `reject`).  
 * `<dkim>`: Результат проверки DKIM (`pass`, `fail`, `policy`).  
 * `<spf>`: Результат проверки SPF (`pass`, `fail`, `neutral`, `softfail`, `temperror`, `permerror`).  
  
**Интерпретация примера:**    
• Отчет показывает данные для домена `example.com` за определенный период.    
• DMARC - политика для домена — `p=none` (мониторинг).    
• С IP-адреса `192.0.2.1` было отправлено 100 писем, которые прошли проверки SPF и DKIM.
• С IP-адреса `198.51.100.1` было отправлено 5 писем, которые не прошли проверки SPF и DKIM.  
  
**Инструменты для анализа:**    
Вместо ручного анализа XML, используйте онлайн-сервисы или специализированное ПО для обработки и визуализации данных из RUA-отчетов. Это значительно упростит анализ и поможет выявить потенциальные проблемы с доставляемостью.