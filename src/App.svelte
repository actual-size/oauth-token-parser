<script>
  import { onMount } from "svelte";
  let token;

  onMount(async () => {
      let query = window.location.hash.substring(1);
      token = query.split("&").map((param) => {
          let [key, value] = param.split("=");
          if (key == "access_token") {
              return value;
         }
     })
 })
</script>

<main>
  <h1>Your token is:</h1>
  <h2>{token}</h2>
</main>
