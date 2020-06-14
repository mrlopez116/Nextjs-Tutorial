# Essentials (NOTES)
**Summary:** These are the different compenents or functionalities we should be using as we develop HIP


## Link

### Usage:

```
import Link from 'next/link';
...
<Link></Link>
```

### Why?: 
Link is a built-in compenent produced by **Next.js** that allows us to render pages on the client-side rather than the server-side. `<Link>` should be replacing all the `<a>` tags that point to another page on our webapp. Next.js has built-in process that make the loading of screen quick and efficient so we do not need to worry about a user waiting for a long time for a page to load. This is done by code-splitting

### TLDR: 
With `<Link>` our page does not reload or fetch to the server. Everything is preloaded efficeintly and we don't have to worry about anything b/c **Next.js** handles the loading and it won't affect load time.


## Head

### Usage:

```
import Head from 'next/head';
...
<Head>
	<title>First Post</title>
</Head>
```

### Why?:
Head is a built-in compenent provided by **Next.js** that allows us to change the Metadata of page use as the `title` and icon shown on the tab header within in the browser.


## Style

### Usage:

```
<style jsx>{`
 	.h1 {
 		font-family: Monospace;
 	}
`}</style>
```

### Why?:
This styling component is using the **styled-jsx** library that has been built-in to **Next.js**. This allows us for easy to use `css` or `scss` files or 'in-file' styling


## CSS Modules

### Example:

Create file as so: `someStyle.module.css`....**needs** to have `.module.css` at the end.
In this file add your all your `css`.

In the file that you want to import the css file import it as such:
`import styles from './someStyle.module.css'` (Please make sure your path is correct. The example here works if `someStyle.module.css` is locate in the same folder as the JS file you are importing it to.)


```
some.js
-----------

import styles from './someStyle.module.css';

function Layout ({ children }) {
	return <div className={styles.container}>{children}</div>;
}

export default Layout;

```

### Explaination: 
CSS Modules automatically create classNames for us and will make sure it never conflicts with anyother class names. These conflicts are called collisions

CSS Modules are extracted from the JavaScript bundles at build time and generate `.css` files that are loaded automatically by **Next.js**.


## _app.js

### Usage
This file needs to be located in the top level of the `pages` directory.

This file allows use to apply whatever is in that file to every other file.
In other words it is the perect place to import styles that we want to be present on every page of our webapp

### Example

```
import '../styles/global.css';

export default function App ({ Component, pageProps }) {
	return <Component {...pageProps} />;
}

```

Now the styles in `global.css` will be applied in every single page of the webapp. This is only special for the `_app.js` file.



------------------------------------------------------------------------

Things that happen in dev mode:
`getStaticProps` runs on each request.

Things that happen in prod mode (at build time):
`getStaticProps` run at build time.



------------------------------------------------------------------------

Server-side rendering functionality. This is used when we need to continually update page contents, not just at build time.


You would have to use this function inorder to use server-side rendering:

```
export async function getServerSideProps(context) {
  return {
    props: {
      // props for your component
    }
  }
}
```































