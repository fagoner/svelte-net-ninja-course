*Looking for a shareable component template? Go here --> [sveltejs/component-template](https://github.com/sveltejs/component-template)*

---

# svelte app

This is a project template for [Svelte](https://svelte.dev) apps. It lives at https://github.com/sveltejs/template.

To create a new project based on this template using [degit](https://github.com/Rich-Harris/degit):

```bash
npx degit sveltejs/template svelte-app
cd svelte-app
```

*Note that you will need to have [Node.js](https://nodejs.org) installed.*


## Get started

Install the dependencies...

```bash
cd svelte-app
npm install
```

...then start [Rollup](https://rollupjs.org):

```bash
npm run dev
```

Navigate to [localhost:5000](http://localhost:5000). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes.

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.


## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).


## Single-page app mode

By default, sirv will only respond to requests that match files in `public`. This is to maximise compatibility with static fileservers, allowing you to deploy your app anywhere.

If you're building a single-page app (SPA) with multiple routes, sirv needs to be able to respond to requests for *any* path. You can make it so by editing the `"start"` command in package.json:

```js
"start": "sirv public --single"
```


## Deploying to the web

### With [now](https://zeit.co/now)

Install `now` if you haven't already:

```bash
npm install -g now
```

Then, from within your project folder:

```bash
cd public
now deploy --name my-project
```

As an alternative, use the [Now desktop client](https://zeit.co/download) and simply drag the unzipped project folder to the taskbar icon.

### With [surge](https://surge.sh/)

Install `surge` if you haven't already:

```bash
npm install -g surge
```

Then, from within your project folder:

```bash
npm run build
surge public my-project.surge.sh
```

## Examples taken from NetNija Svelte Tutorial for beginners


### Two way data-binding
```
<input type="text" bind:value={firstName}>
```

### Reactive values
```
  $: fullName = `${firstName} ${lastName}`
```

### Reactive statements
```
$: { 
  console.log(beltColor);
  console.log(fullName );
}
```

### Loops with else(if there is no values to show)
```
<script>
	let people  = [
		{ name: 'Yoshi', beltColor: 'black', age: 25, id: 1},
		{ name: 'Mario', beltColor: 'yello', age: 31, id: 2}
	]
</script>

<main>
	<div>
		{#each people as person (person.id)}
			<div>
				<h4>{person.name}</h4>
			</div>
		{:else}
			<p>Ther are no people to show</p>
		{/each}
		
	</div>
</main>
```


### Delete elements
```
const handleClick = (id) => {
 people = people.filter(person => person.id !== id);
	}
</script>

<main>
	...
<button on:click={()=>handleClick(person.id)}>
  Delete
</button>
```

### Conditional checking

```
...
	let num = 2;
</script>

{#if num > 20}
	<p>Greater than 20</p>
{:else if num > 5 }
	<p>Greater than 5</p>
{:else}
	<p>Not greather than 5</p>
{/if}
```