# `@lafrenchtech/open-graph`

A tiny Node.js microservice to scrape open graph data with joy.

Running this microservice you won't need a backend solely to get some meta information about links your users submit. Press the deploy button below and show your users what the links they're clicking on contain!

## Deployment

Your own `@lafrenchtech/open-graph` is one click away:

[![Deploy to now](https://deploy.now.sh/static/button.svg)](https://deploy.now.sh/?repo=https://github.com/lafrenchtech/open-graph)

You can also deploy with a single command from the terminal (assuming you have [`now`](https://now.sh) installed):

```sh
now lafrenchtech/open-graph
```

## Alias Deploy URL

* see: https://zeit.co/docs/features/aliases#creating-aliases

Aliases are managed by invoking the command `now alias`, which has the following syntax:
`now alias <SOURCE URL | ID> <TARGET SUBDOMAIN | DOMAIN>`

For example, let's say you want https://get-started-basic-etjnigdrkz.now.sh to be accessible by the alias get-started-basic.now.sh.

## Deps

```json
  "dependencies": {
    "got": "^8.0.1",
    "memory-cache": "^0.1.6",
    "metascraper": "^3.0.0",
    "micro": "^7.0.6"
  },
  "devDependencies": {
    "nodemon": "^1.11.0",
    "standard": "^8.6.0"
  }
```

## Usage

To get the data for a given URL, for example `mxstbr.blog`, simply add that URL (safely escaped) to the `url` query parameter:

```sh
https://your-url.now.sh/?url=http://mxstbr.blog
```

And you will get the parsed data in the following format:

```JSON
{
	"author": null,
	"date": "2017-02-16T11:00:00.000Z",
	"description": "Fresh thinking and expert tips about HTML, CSS, JavaScript and other web technologies.",
	"image": "http://mxstbr.blog/social_media.png",
	"publisher": "<mxstbr/>",
	"title": "<mxstbr/>",
	"url": "http://mxstbr.blog/"
}
```

> Note: Not all of this, or even more, data might be available depending on the `meta` tags the page has in its HTML. (see [`metascraper`](https://github.com/ianstormtaylor/metascraper/tree/master/lib/rules) for the full list of supported properties)

We infer the data from more places than just the open graph meta tags, we also support twitter meta tags and fallback to standard HTML tags like e.g. the `title` tag if no open graph data was specified. Results are cached in memory for 24 hours, which means calling this with the same URL repeatedly won't have a large impact on your server!

## Development

```sh
git clone git@github.com:lafrenchtech/open-graph.git
npm run dev
```

The server will then be listening at `localhost:3000`.

## Updating

The `master` branch of this repository is what you will be deploying. To update to a new version with potential bugfixes, all you have to do is run the `now` command again and change the URL you call in your app! 👌

## License

Copyright (c) 2017 Maximilian Stoiber, licensed under the MIT license. See [LICENSE.md](LICENSE.md) for more information.
