RUF (Forensic Reports) предоставляют детальную информацию о каждом отдельном письме, которое не прошло DMARC - проверку. Они отправляются в формате XML и могут быть довольно объемными. Важно понимать, что не все почтовые серверы отправляют RUF-отчеты.  
  
**Пример отчета RUF:**  

```
<?xml version="1.0" encoding="UTF-8" ?>
<feedback>
 <report_metadata>
 <org_name>Example Receiving Domain</org_name>
 <email>forensic@example.net</email>
 <report_id>87654321</report_id>
 <date_range>
 <begin>1679145600</begin>
 <end>1679145600</end>
 </date_range>
 </report_metadata>
 <policy_published>
 <domain>example.com</domain>
 <adkim>r</adkim>
 <aspf>r</aspf>
 <p>quarantine</p>
 <sp>none</sp>
 <pct>100</pct>
 </policy_published>
 <record>
 <row>
 <source_ip>192.0.2.2</source_ip>
 <count>1</count>
 <policy_evaluated>
 <disposition>quarantine</disposition>
 <dkim>fail</dkim>
 <spf>fail</spf>
 <reason>
 <type>dmarc</type>
 <code>001</code>
 <comment>dmarc fail, see other results</comment>
 </reason>
 </policy_evaluated>
 <identifiers>
 <header_from>example.com</header_from>
 </identifiers>
 <auth_results>
 <dkim>
 <domain>example.net</domain>
 <result>fail</result>
 <selector>selector1</selector>
 </dkim>
 <spf>
 <domain>example.org</domain>
 <result>fail</result>
 </spf>
 </auth_results>
 </row>
 </record>
</feedback>
```

  
**Как читать отчет RUF:**    
1. `<report_metadata>`**:** Метаданные отчета (аналогично RUA).    
2. `<policy_published>`**:** Опубликованная DMARC-политика (аналогично RUA).    
3. `<record>`**:** Информация о письме, не прошедшем проверку.  
 * `<row>`: Данные о письме.  
 * `<source_ip>`: IP-адрес отправителя.  
 * `<count>`: Всегда 1, так как RUF относится к одному письму.  
 * `<policy_evaluated>`: Результаты проверки.  
 * `<disposition>`: Действие, предпринятое сервером (`none`, `quarantine`, `reject`).  
 * `<dkim>`: Результат DKIM.  
 * `<spf>`: Результат SPF.  
 * `<reason>`: Дополнительная информация о причине неудачи.  
 * `<identifiers>`: Идентификаторы письма.  
 * `<header_from>`: Значение заголовка `From`.  
 * `<auth_results>`: Детальные результаты аутентификации.  
 * `<dkim>`: Информация о проверке DKIM.  
 * `<domain>`: Домен, использованный для DKIM-подписи.  
 * `<result>`: Результат проверки.  
 * `<selector>`: Селектор DKIM.  
 * `<spf>`: Информация о проверке SPF.  
 * `<domain>`: Домен, использованный для проверки SPF.  
 * `<result>`: Результат проверки.  
  
**Интерпретация примера:**    
• Письмо от `192.0.2.2` с заголовком `From: example.com` не прошло DMARC-проверку.   
• DMARC-политика — `p=quarantine`, поэтому письмо, вероятно, было помечено как спам.    
• Проверки DKIM и SPF завершились неудачно.    
• DKIM-подпись была с доменом `example.net`, а SPF-проверка проводилась для `example.org`. Это указывает на то, что письмо, скорее всего, поддельное.  
  
**Важно:** RUF-отчеты содержат много технических деталей. Для эффективного анализа используйте специализированные инструменты, которые помогут вам разобраться в данных и выявить причины проблем с доставляемостью. Они преобразуют XML в удобный для чтения формат и предоставят рекомендации по устранению неполадок.