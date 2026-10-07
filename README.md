# personal-digest

A small Ruby script that researches the topics you care about with Claude
(web search + web fetch) and emails you a weekly digest.

Each topic is a Markdown file in `topics/` with its own research instructions.
Shared guidelines live in `guidelines.md`. The script skips links you've
already been sent and adds an estimated API cost to the bottom of each digest.

## Requirements

- Ruby 3.4 (a `mise.toml` is included)
- An [Anthropic API key](https://console.anthropic.com/) in `ANTHROPIC_API_KEY`
- [msmtp](https://marlam.de/msmtp/), set up to send mail, with its password in
  the system keyring (`secret-tool`)

## Setup

```sh
mise install
bundle install
cp config.example.yml config.yml   # set recipient and keyring_lookup
```

## Usage

```sh
bin/digest --dry-run               # print the digest instead of emailing it
bin/digest --topic ruby-rails      # run a single topic
bin/digest                         # research all enabled topics and email the digest
```

To add a topic, copy `topics/_template.md` to `topics/<slug>.md` and edit it.
To get a weekly digest, run `bin/digest` from cron or a systemd timer.

## License

[MIT](LICENSE)
