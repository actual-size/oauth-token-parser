<script>
  import { onMount } from "svelte";
  export let date;
  let token;

  onMount(async () => {
    const res = await fetch("/api/date");
    const newDate = await res.text();
    date = newDate;
  });
  onMount(async () => {
      let query = window.location.search.substring(0);
      token = query.split("&").map((param) => {
          let (key, value) = param.split("=");
          if (key == "code") {
              return value;
         }
     })
 })
</script>

<main>
  <h1>Svelte + Node.js API</h1>
  <h2>
    Deployed with
    <a href="https://vercel.com/docs" target="_blank" rel="noreferrer noopener">
      Vercel
    </a>
    !
  </h2>
  <p>
    <h1>{token}</h1>
  </p>
  <br />
  <h2>The date according to Node.js is:</h2>
  <p>{date ? date : 'Loading date...'}</p>
</main>
