<script>
  import http from "axios";
  import Header from "./Header.svelte";
  import InputBottom from "./InputBottom.svelte";
  import List from "./List.svelte";

  let listData = [];

  const answer = value => {
    http
      .get(`//127.0.0.1:9000?question=${value}`)
      .then(function(response) {
        console.log(response);
        const data = {
          class: "message1",
          info: response.data.msg
        };
        listData = [...listData, data];
        const scroll = setInterval(() => {
		  window.scrollTo(0, document.body.scrollHeight);
		  clearInterval(scroll)
		}, 100);
      })
      .catch(function(error) {
        console.log(error);
      });
  };

  const getValue = value => {
    const data = {
      class: "message2",
      info: value
    };
    listData = [...listData, data];
    answer(value);
    console.log(listData);
    window.scrollTo(0, document.body.scrollHeight);
  };
</script>

<style>
  main {
    text-align: center;
    /* width: 100vw; */
  }
</style>

<main>
  <Header title={'AI'} />
  <List bind:data={listData} />
  <InputBottom {getValue} />
</main>
