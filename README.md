Fork of [Edward Irby's](https://www.npmjs.com/~edwardirby) [jsontosass-loader](https://www.npmjs.com/package/jsontosass-loader)
-------------------------------------------------------------------------------------------------------------------------------

# JSON to Sass loader for Webpack

This loader converts your JSON or module.export'ed JS variables into SCSS variables.

### Installation

`npm install sass-json-loader --save-dev`

## Usage

Add this to loader after `sass-loader` in your Webpack configuration file:

``` javascript
var sassVars = 'path/to/your/vars.json';

module.exports = {
    /* ... */
    {
        test: /\.scss$/,
        loader: extractMain.extract({
            fallback: 'vue-style-loader',
            use: [
                'css-loader',
                'sass-loader',
                {
                    loader: 'sass-json-loader',
                    options: { path: sassVars }
                }
            ]
        })
    },
    /* ... */
}
```

**Input [YourVars.json file]**
``` json
{
"breakpoints":{
    "portraitS": "320px",
    "portraitM": "360px",
    "portraitL": "414px",
  },
  "localNavHeight":"50px",
}
```

OR

**[YourVars.js file]**
``` javascript
{
module.exports = {
	breakpoints: {
		portraitS: '320px',
		portraitM: '360px',
		portraitL: '414px'
	},
	deepObject: {
		a: {
			b: 'c'
		}
	}
};
```

**Output SCSS**
``` scss
$breakpoints:(portraitS:320px,portraitM:360px,portraitL:414px);
$localNavHeight:50px;
```


Originally forked from gist: [jsonToSassVars](https://gist.github.com/Kasu/ea4f4861a81e626ea308) and [prepend-loader](https://gist.github.com/Kasu/29452051023ff5337bd7)

## License

MIT (http://www.opensource.org/licenses/mit-license.php)
