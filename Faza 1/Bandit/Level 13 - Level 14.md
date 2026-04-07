Link: [Level 14](https://overthewire.org/wargames/bandit/bandit14.html)

Zadaniem jest pozyskanie hasła z  **/etc/bandit_pass/bandit14** ale może ono zostać odczytane tylko jako bandit14. Aby zalogować się jako bandit14 musimy użyć klucza ssh.

1. Listuję katalog by znaleźć klucz `ls`
2. Sprawdzam jego uprawnienia `ls -la`
3. Nie mogę się zalogować jako inny user z poziomu localhost więc się wylogowuję `exit`
4. Na lokalnej maszynie za pomocą `scp` pobieram plik z kluczem `scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .`
5. Za pomocą `ssh` z flagą `-i` loguję się jako bandit14 `ssh bandit.labs.overthewire.org -p 2220 -l bandit14 -i .\sshkey.private`
6. Odczytuję hasło `less  /etc/bandit_pass/bandit14`