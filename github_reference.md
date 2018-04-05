# Referencia de GitHub

## Links útiles

- https://www.atlassian.com/git
- [atlassian cheatsheet](atlassian-git-cheatsheet.pdf)
- Para usar SSH sobre el puerto HTTPS (si tenes firewall en el laburo)
  - https://help.github.com/articles/using-ssh-over-the-https-port/
- Syntax
  - highlighting: https://help.github.com/articles/creating-and-highlighting-code-blocks/
  - Basic: https://help.github.com/articles/basic-writing-and-formatting-syntax/
  - Emoji: https://www.webpagefx.com/tools/emoji-cheat-sheet/
  - Mastering: https://guides.github.com/features/mastering-markdown/
  - Tablas: https://help.github.com/articles/organizing-information-with-tables/
  - Mas preciso:
    - https://daringfireball.net/projects/markdown/syntax
    -
- Tutoriales
  - http://jmcglone.com/guides/github-pages/
- Editor online de markdown
  - [stackedit.io](https://stackedit.io/editor#fnref:footnote)



## Códigos básicos
Bajar código desde el respositorio:

```bash
git clone git@github.com:marceluda/personal_notes.git
```
Descartar los últimos cambios después del commit

```bash
git reset HEAD --hard
```


### Seteo de gh-pages
```bash

git clone git@github.com:marceluda/rp_scope_lock.git
git checkout --orphan gh-pages
vim index.md
git commit -m "initial commit"
git push -u origin gh-pages
```

Luego cambias en el settings de github.

Si al hacer esto te pide login, capaz estas usasndo https. En ese caso, cambiate a ssh:
```bash
git config -l
git config remote.origin.url git@github.com:marceluda/rp_lock-in_pid.git
```


### SSH oara github
crear key

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Agregar [key a github](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

```bash
sudo apt-get install xclip
# Downloads and installs xclip. If you don't have `apt-get`, you might need to use another installer (like `yum`)
xclip -sel clip < ~/.ssh/id_rsa.pub
# Copies the contents of the id_rsa.pub file to your clipboard
```
Ir a [github.com/settings/keys](https://github.com/settings/keys)

y pegar

