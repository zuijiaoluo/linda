# Linda

[![Build Status](https://travis-ci.org/kpashka/linda.svg)](https://travis-ci.org/kpashka/linda) [![Docker Repository on Quay](https://quay.io/repository/kpashka/linda/status "Docker Repository on Quay")](https://quay.io/repository/kpashka/linda)
 [![GoDoc](https://godoc.org/github.com/kpashka/linda?status.svg)](https://godoc.org/github.com/kpashka/linda)

Multi-platform, highly configurable conference bot.

Example usage:

<p align="center">
	<img src="https://raw.github.com/kpashka/linda/master/static/example.png">
</p>

Navigation:

1. [Features](#features)
1. [Limitations](#limitations)
1. [Configuration](#configuration)
1. [Installation](#installation)
1. [Docker](#docker)

## Features

* Different adapters support:
	* [Slack](https://api.slack.com/bot-users)
	* [Telegram](https://core.telegram.org/bots/api)<sup>beta</sup> 
* Configurable commands:
	* [`bully`](commands/bully) - reacts with predefined phrase to matched text.
	* [`copycat`](commands/copycat) - returns same text, can be powerful in combination with filters.
	* [`help`](commands/help) - prints information about instantiated commands.
	* [`postman`](commands/postman) - grabs latest unread item from RSS/Atom feed.
	* [`proxy`](commands/proxy) - fetches JSON document from URL, returns computed template.
* Built-in filters:
	* `base64` - encodes input text to base64.
	* `md5` - calculates md5 sum of input text.
	* `translit` - transliterates input text.
	* `uppercase` - converts input text to uppercase.
* User-friendly:
	* Configurable greeting and farewell messages.
	* Configurable reaction to user status change.
	* Has option to get configuration file by provided URL.
	* `shy mode` in case of being annoyed by large amount of greetings.

## Limitations

Because of the fact that different chat services have different protocols and available options, some usage limitations are present. The table of differences lies below:

| Feature                               | [Slack](https://api.slack.com/bot-users) | [Telegram](https://core.telegram.org/bots/api) |
| ------------------------------------- | ---------------------------------------- | ---------------------------------------------- |
| All types of commands                 | :white_check_mark: Supported             | :white_check_mark: Supported                   |
| Specific channel to listen            | :white_check_mark: Supported             | :x: (Currently Linda responds to everyone)     |
| Greetings & farewells                 | :white_check_mark: Supported             | :x: (Possible, but not yet implemented)        |
| Status change reactions               | :white_check_mark: Supported             | :x: (Possible, but not yet implemented)        |

## Configuration

* See [linda.example.toml](linda.example.toml) for configuration example.

## Installation

Install [glide](https://github.com/Masterminds/glide) tool.

Build and run:

	$ go get github.com/kpashka/linda
	$ export LINDA_CONFIG=<path_or_url_to_your_configuration_file>
	$ linda -c $LINDA_CONFIG

## Docker

Use the automated build from [Docker Registry](https://quay.io/repository/kpashka/linda).

	$ make pull
	$ LINDA_CONFIG=<url_to_your_configuration_file> make up
