gulp-maven-deploy
=================

A [Gulp](//gulpjs.com/) wrapper for the [maven-deploy](https://www.npmjs.org/package/maven-deploy) module. Enables you to have projects which are built with Gulp, but deploys to Maven repositories. 

[![Build Status](https://api.travis-ci.org/finn-no/gulp-maven-deploy.png?branch=master)](https://travis-ci.org/finn-no/gulp-maven-deploy)
[![NPM](https://nodei.co/npm/gulp-maven-deploy.png?stars=true&downloads=true)](https://npmjs.org/package/gulp-maven-deploy)

All the samples below requires a basic understanding of [Gulp](//gulpjs.com/) and [Maven](http://maven.apache.org/). Please look at the documentation for those projects for details. 

## Installing

	$ npm install gulp-maven-deploy --save-dev

## Sample usage in a gulpfile.js

Configuring a task for deploying to a Maven proxy:

	var maven = require('gulp-maven-deploy');

	gulp.task('deploy', function(){
		gulp.src('.')
		.pipe(maven.deploy({
			'config': {
				'groupId': 'com.mygroup',
				'type': 'war',
				'repositories': [
					{
						'id': 'some-repo-id',
						'url': 'http://some-repo/url'
					}
				]
			}
		}))
	});

A task running a local Maven install:

	var maven = require('gulp-maven-deploy');

	gulp.task('deploy-local', function(){
		gulp.src('.')
		.pipe(maven.install({
			'config': {
				'groupId': 'com.mygroup',
				'type': 'war'
			}
		}))
	});

Note: A local install in Maven means it is only available on your machine. A deployment is different as it means you ship the artifact off to some remote repository.

## Running tests

	$ npm test

## Contributions

All pull requests and issues are welcome!

Big thanks to [Gregers](https://github.com/gregersrygg) for making the [maven-deploy](https://www.npmjs.org/package/maven-deploy) module.