# Asyncron™

> a synchronized checklist verification \
> (lightweight Dead Man's Snitch alternative)


## Premise

1. Give an interval on how often some task must be accomplished, and pinged
2. Check periodically


## Installation

- put on a local network, or some subdomain prob

- script only needs read+write access to the current directory, to keep track of tasks and pings

- no database needed

- no javascript needed


## Usage

1. open script's url (eg. `http://ping.local`) and create some tasks
2. automate verification of accomplishments (like cron scripts)
3. for manual completion – click on the task and press the «Ping Manually» button


### shell scripts and crontab

> `crontab -l`

```sh
15 10 * * *  ~/backup.sh  &&  curl -X PATCH 'http://ping.local/?backup'
```


## http API

- `GET` – returns `1` if task was pinged and interval has not yet expired, otherwise `0`
- `POST` – create/reactivate
- `PUT` – update description and/or interval
- `PATCH` – ping a completion
- `DELETE` – deactivate

more details in the source code
