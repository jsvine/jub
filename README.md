# jub

As in, "get the jub done." It's a shell script that automatically grabs the latest versions of jQuery (j), Underscore.js (u), and Backbone.js (b), so you can get on with prototyping. Prefer another combination of libraries? No problem; __jub__ is easily configurable.

## Basic Usage

    chmod +x jub
    ./jub > path/to/my/javascript/folder/jub.js

## Configuration

By default, __jub__ downloads and concatenates jQuery, Underscore.js, and Backbone.js — in that order, using `curl`. There are a few ways you can change this default behavior.

### Downloading different libraries

The first argument passed to __jub__ defines the libraries it will download. So `./jub jub` does the same thing as plain-old `./jub`. And `./jub ujb` would `curl` Underscore first, followed by jQuery and Backbone. And `./jub j` would download just jQuery. So far, __jub__ supports the following libraries, in alphabetical order:

- `b`: [Backbone.js](http://documentcloud.github.io/backbone/backbone-min.js)
- `d`: [d3.js](https://raw.github.com/mbostock/d3/master/d3.min.js)
- `j`: [jQuery](http://code.jquery.com/jquery-latest.js)
- `m`: [Moment.js](https://raw.github.com/moment/moment/master/moment.js)
- `q`: [Queue.js](https://raw.github.com/mbostock/queue/master/queue.min.js)
- `u`: [Underscore.js](http://underscorejs.org/underscore-min.js)
- `z`: [Zepto.js](http://zeptojs.com/zepto.min.js)

So `./jub md` would fetch Moment.js and d3.js. And so on.

There's room for more, obviously. If you think a particularly common library belongs in __jub__, [file an issue](https://github.com/jsvine/jub/issues) or [make a pull request](https://github.com/jsvine/jub/pulls). Or just edit your local [jub script](https://github.com/jsvine/jub/blob/master/jub). Adding a library requires just a single line of text.

### Customizing `curl`

Stuck behind a firewall? Just want `curl` to shut its verbose mouth? No problem. Additional arguments to `jub` get passed directly to `curl`. For example...

To trigger `curl`'s "silent" mode:

    ./jub jub -s

*Notice that, in order for `-s` not to be interpreted as libraries for `jub` to download, you must explictly list the libraries first.*

To use silent mode and also use a proxy to download just Underscore:

    ./jub u -s --proxy http://MYPROXY.WHATEVER:PORT

## Caveats

- __jub__ automatically fetches code from third-party servers. While it does not execute the code, you should still be aware of the potential security risks involved.

- __jub__ automatically fetches the latest versions of each library, so it's really just for prototyping. For production, you'll probably want more control over versions than __jub__ is willing to offer.

- __jub__ might not actually save you time. Consult [this chart](http://xkcd.com/1205/) to learn more.

