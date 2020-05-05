<script>
  import http from "axios";
  import Header from "./Header.svelte";
  import InputBottom from "./InputBottom.svelte";
  import List from "./List.svelte";
  import InputVoice from "./InputVoice.svelte";

  let listData = [];
  let inputState = 1

  const answer = value => {
    http
      .get(`//39.108.101.202:9000?question=${value}`)
      .then(function(response) {
        console.log(response);
        const data = {
          class: "message1",
          info: response.data.msg
        };
        listData = [...listData, data];
        const scroll = setInterval(() => {
          window.scrollTo(0, document.body.scrollHeight);
          clearInterval(scroll);
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

  const getVoiceValue = value => {
    const data = {
      class: "message3",
      info: ''
    };
    listData = [...listData, data];
    answer(value);
    console.log(listData);
    window.scrollTo(0, document.body.scrollHeight);
  };
  const changeInput = value => {
    console.log(value);
    inputState = value
  };
</script>

<style>
  main {
    text-align: center;
  }
</style>

<main>
  <Header title={'医疗导诊AI'} />
  <List bind:data={listData} />
  {#if inputState === 0}
    <InputBottom {getValue} {changeInput}  />
  {:else}
    <InputVoice {getVoiceValue} {changeInput} />
  {/if}
</main>
