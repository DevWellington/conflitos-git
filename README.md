Resolvendo conflitos no Git
=============

Exemplo simples de como resolver um conflito de um merge no git.

Abaixo segue comandos executados para gerar e resolver um conflito:

```shell

mkdir conflitos-git
cd conflitos-git/
git init
touch index.html
mkdir js css
touch css/style.css
touch js/common.js
git add index.html
git commit -m "add index"
git add css/
git commit -m "add style css"
git add .
git commit -m "add scripts javascript"
vim index.html
	<html>
		<head>
			<title>Teste de conflitos do Git</title>
		</head>
		<body>
			<h1>Teste de conflitos no Git</h1>
		</body>
	</html>
	
git commit -a -m "add conteudo"
git checkout -b branch_teste
	vim index.html
		<div>
			Inicio dos testes
		</div>
	
	git add index.html
	git commit -m "Add div"
	git checkout master
vim index.html
	<div id"container">
		<p>Inicio dos Testes</p>
	</div>
	
git commit -a -m "add conteudo in master"
git merge branch_teste
	Auto-merging index.html
	CONFLICT (content): Merge conflict in index.html
	Automatic merge failed; fix conflicts and then commit the result.

$ cat index.html
	<html>
		<head>
			<title>Teste de conflitos do Git</title>
		</head>
		<body>
			<h1>Teste de conflitos no Git</h1>
	<<<<<<< HEAD
			<div id"container">
				<p>Inicio dos Testes</p>
	=======
			<div>
				Inicio dos testes
	>>>>>>> branch_teste
			</div>
		</body>
	</html>
	
	
	TO
	
	<html>
		<head>
			<title>Teste de conflitos do Git</title>
		</head>
		<body>
			<h1>Teste de conflitos no Git</h1>
			<div id"container">
				<p>Inicio dos Testes</p>
			</div>
		</body>
	</html>	
	
	
git add index.html
git commit -m "resolved conflits"
git merge branch_teste
git log --stat

	commit 7b9f1703ba4995c0b0adec291499ef2204e2c002
	Merge: 843681a c15c7f8
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:28:13 2014 -0200

		resolved conflits

	commit 843681a5b09eab21f614c54e67fe324d79f83935
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:19:20 2014 -0200

		add conteudo in master

	 index.html | 3 +++
	 1 file changed, 3 insertions(+)

	commit c15c7f8307878e7fcb1396c3d7204f8248161fa0
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:16:04 2014 -0200

		Add div

	 index.html | 3 +++
	 1 file changed, 3 insertions(+)

	commit 72de97965dae295a95ff4ed7fdcf660cecd9e7d8
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:14:21 2014 -0200

		add conteudo

	 index.html | 8 ++++++++
	 1 file changed, 8 insertions(+)

	commit a7e1e3cef0c6ff2507e61007a076e6bb91eed426
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:01:00 2014 -0200

		add scripts javascript

	 js/common.js | 0
	 1 file changed, 0 insertions(+), 0 deletions(-)

	commit a688a8d357e5e7284accf2bae16af0d29df21cd9
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:00:48 2014 -0200

		add style css

	 css/style.css | 0
	 1 file changed, 0 insertions(+), 0 deletions(-)

	commit 55198791da3776b6400c9b60d74b2d2f0bcd9c9c
	Author: Wellington Ribeiro <devwellington@gmail.com>
	Date:   Tue Nov 18 16:00:37 2014 -0200

		add index

	 index.html | 0
	 1 file changed, 0 insertions(+), 0 deletions(-)



```
