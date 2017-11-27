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
- Tutoriales
  - http://jmcglone.com/guides/github-pages/
- Editor online de markdown
  - [stackedit.io](https://stackedit.io/editor#fnref:footnote)



## Códigos básicos
Bajar código desde el respositorio:

```bash
git clone git@github.com:marceluda/personal_notes.git
```
Descartar los ultimos cambios despues del commit

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
