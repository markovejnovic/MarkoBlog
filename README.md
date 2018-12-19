# MarkoBlog

_MarkoBlog_ is a Hugo static website about myself.

## Getting Started

These instructions will get you a copy of the project up and running on your
local machine for development and testing purposes. See deployment for notes on
how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them

```
hugo
```

### Installing

After downloading `hugo`, clone the repository:

```bash
git clone git@github.com/markovejnovic/MarkoBlog
```

Next, `cd` into the directory:
```bash
cd MarkoBlog
```

Now, all you have to do is:
```bash
hugo
```

You should get something similar to:
```
                   | EN  
+------------------+----+
  Pages            | 67  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 54  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 155 ms
```

This will create the final static website in `public/`.

## Deployment

I recommend deploying the website with `nginx`. A possible configuration is:

```
/etc/nginx/conf.d/markovejnovic.conf
```
:
```
server {
	server_name markovejnovic.com www.markovejnovic.com;

	root /var/www/markovejnovic;
	index index.html;

	location / {
		try_files $uri $uri/ =404;
	}
}
```

Finally, don't forget to use `certbot` to get a free `https` certificate:
```
certbot --nginx
```

## Built With

* [Hugo](https://gohugo.io/) - The world’s fastest framework for building websites
* [cocoa-eh](https://github.com/markovejnovic/cocoa-eh) - My modified version
  of the original [cocoa-eh](https://github.com/mtn/cocoa-eh-hugo-theme) _hugo_
theme.

## License

This project is licensed under the AGPLv3 License - see the
[LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* [Purplebooth](https://gist.github.com/PurpleBooth) for her fantastic
  [README.md
template](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
