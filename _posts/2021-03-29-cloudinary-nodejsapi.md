---
layout: post
title: "Cloudinary nodejs api"
date: 2020-03-29 15:01:02
image: '/assets/img/cloudinary.jpg'
description: "Webstorm no console macos."
tags:
- webstorm
- macos
- console
---

<img src="/assets/img/cloudinary.jpg" style="width: 286px; height: 180px;">


## Instalação

<p> O primeiro passo é instalar as dependecias:</p>
{% highlight zsh %}
npm install express
npm install multer
npm install cloudinary
{% endhighlight %}

<br>

<p> criar o projeto</p>

{% highlight zsh %}

npm init

{% endhighlight %}

<p>criar file de nome index.js com o seguinte conteudo</p>

<script src="https://gist.github.com/Ahnix/2b5c97a3cfbdd0acb9fbcf146aa783b1.js"></script>

<p>O seu package.json deve conter o seguinte conteudo</p>

{% highlight %}


{
"name": "apinodejs-cloudinary",
"version": "1.0.0",
"description": "",
"main": "index.js",
"scripts": {
"start": "node index.js",
"dev": "nodemon index.js"
},
"dependencies": {
"cloudinary": "^1.11.0",
"express": "^4.16.3",
"multer": "^1.3.1"
},
"author": "Ramon Almeida",
"license": "ISC"
}

{% endhighlight %}

<p>basta rodar o npm i em seguida node index.js, sua api de upload estara pronta.
vale ressaltar que no index deve ser preenchido os dados de acesso ao cloudinary.
</p>

