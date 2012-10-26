
# Github Api odule for Zend Framework 2

Version 0.0.1 Created by [Martin Shwalbe](https://hounddog.github.com)

## Introduction

EdpGithub is a Wrapper for the Github Api  based on Zend Framework 2  which uses [Github API v3](http://developer.github.com/v3/).

## Installation

### Main Setup

1. Clone this project into your `./vendor/` directory and enable it in your
   `application.config.php` file.

### Usage

## Basic Usage

Here is short example on how to use

    $client = $serviceManager->get('EdpGithub\Client');
    $repos = $client->api('user')->repos('hounddog');

This would fetch all the  Repositories for the user Hounddog

## Authentication

To use functionality which needs Authentication you have to first authenticate

    $client = $serviceManager->get('EdpGithub\Client');
    $client->authenticate('url_token', 'access_token');
    $repos = $client->api('current_user')->repos();

You can also listen to the Event <em>'EdpGithub\Client', 'api'</em>

    $em->attach('EdpGithub\Client', 'api', function($e) use ($sm) {
        $client = $e->getTarget();
        $client->authenticate('url_token', $token /* your access_token here */);
    } );

## Documentation
Please refer to the [Wiki](https://github.com/Hounddog/EdpGithub/wiki) for a more detailed Documentation