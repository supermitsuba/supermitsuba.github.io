---
id: 18
title: Grunt, an awesome build tool
date: 2014-12-14T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Grunt,_an_awesome_build_tool
permalink: /2014/12/14/grunt-an-awesome-build-tool/
categories:
  - javascript
  - node.js
tags:
  - automation
  - grunt
  - javascript
  - node.js
---
 <p> I have been working with <a href="/title/TypeScript">TypeScript</a> recently. The pain of working with TypeScript is that you have to compile it every time you make a change. This means switching from your text editor, to your cmd window, run the command, then refresh your browser. With grunt, it can watch these types of files, less files, and more, all to build and update them so you can concentrate on development and debugging. </p> <p> To get started with grunt, you can start off by installing grunt, using npm. </p> <pre class="formatCode"> npm install -g grunt-cli </pre> <p> Next, you should create a package.json file. This will make installing dependencies easier for other devs. You can do this by typing in: </p> <pre class="formatCode"> npm init </pre> <p> Fill in the questions, and you will have your npm package list, package.json. Now, when you start adding grunt packages, you can add them to your package.json. This will keep track of dependencies. Here is how you can add a package to your package.json: </p> <pre class="formatCode"> npm install grunt-contrib-jshint --save-dev </pre> <p> This adds grunt-contrib-jshint package to package.json and allows you to start using it in your grunt server. For more information about grunt setup, visit the site <a href="http://gruntjs.com/getting-started">here</a>. </p> <p> After getting that setup going, now you can create a gruntfile.js and start adding modules to it: </p> <pre class="formatCode"> var path = require('path'); module.exports = function(grunt) { // Load Grunt tasks declared in the package.json file require('matchdep').filterDev('grunt-\*').forEach(grunt.loadNpmTasks); // Configure Grunt grunt.initConfig({ express: { all: { options: { bases: [path.resolve('./public'), path.resolve('./view')], server: path.resolve('./server.js'), port: 8081 } } }, typescript: { default: { src: ['lib/\*\*/\*.ts'], dest: 'public/js/app.js', options: { module: 'amd', target: 'es5', ignoreError: true } } }, // grunt-watch will monitor the projects files // https://github.com/gruntjs/grunt-contrib-watch watch: { typescript: { files: '*\*/\*.ts', tasks: ['typescript'] } }, // grunt-open will open your browser at the project's URL // https://www.npmjs.org/package/grunt-open open: { all: { path: 'http://192.168.10.103:8081/' } } }); // Creates the \`server\` task grunt.registerTask('server', [ 'typescript', 'express', 'open', 'watch' ]); }; </pre> <p> This is an example of a typescript project I have been working on. Let&#8217;s talk about each piece. The best part to start with is the very end. You register a task called server. This task starts the typescript section first, then starts an express server, opens a web server and watches for any typescript file changes. </p> <p> So, if you want to just build and deploy code, you can create a deploy and dev task, instead of a server task. Very customizable, and most of the grunt packages have lots of documentation, so combine grunt with any development or coding you have going on. </p>