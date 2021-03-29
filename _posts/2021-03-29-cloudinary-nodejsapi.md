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

{% highlight %}

const express = require('express')
const app = express()

// MULTER
const multer = require('multer')

const storage = multer.diskStorage({
destination: function(req, file, cb) {
cb(null, 'uploads/')
},
filename: function(req, file, cb) {
console.log(file)
cb(null, file.originalname)
}
})

// POST ROUTE
app.post('/upload', (req, res, next) => {
const upload = multer({ storage }).single('foldertoupload')
upload(req, res, function(err) {
if (err) {
return res.send(err)
}

    console.log('file uploaded to server')
    console.log(req.file)

    // SEND FILE TO CLOUDINARY
    const cloudinary = require('cloudinary').v2
    cloudinary.config({
      cloud_name: 'nomecloudinary',
      api_key: 'chavecloudinary',
      api_secret: 'suakeycloudinary'
    })

    const path = req.file.path
    const uniqueFilename = new Date().toISOString()

    cloudinary.uploader.upload(
      path,
      { public_id: `${uniqueFilename}` }, // directory and tags are optional
      function(err, image) {
        if (err) return res.send(err)
        console.log('file uploaded to Cloudinary')

        var fs = require('fs')
        fs.unlinkSync(path)

        res.json(image)
      }
    )
})
})

app.listen(3000)

{% endhighlight %}

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

