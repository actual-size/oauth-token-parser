<script>
  import { onMount } from "svelte";
  let token;

  onMount(async () => {
      let query = window.location.search.substring(1);
      token = query.split("&").map((param) => {
          let [key, value] = param.split("=");
          console.log(param)
          if (key == "code") {
              return value;
         }
     })
 })
</script>

<main>
  <h1>Your token is:</h1>
  <h2>{token}</h2>
</main>
