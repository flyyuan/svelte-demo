<script>
  export let getValue;
  let text = '';
</script>

<style>
  .input {
    display: flex;
    align-content: space-around;
    justify-items: center;
    padding: 4px;
    width: 100%;
    position: fixed;
    bottom: 0px;
    height: 6vh;
    background: rgb(226, 214, 214);
  }
  input {
    border: 1px white solid;
    border-radius: 3px;
    outline: none;
    width: 80%;
    height: 85%;
    margin-right: 5px;
    font-size: 20px;
  }
  span {
    height: 6vh;
    margin-right: 5px;
    width: 20%;
    padding: 8px;
    color: #ffffff;
    background-color: #1aad19;
    box-sizing: border-box;
    text-align: center;
    text-decoration: none;
    border-radius: 5px;
    -webkit-tap-highlight-color: transparent;
    overflow: hidden;
    line-height: 4vh;
  }
</style>

<div class="input">
  <input bind:value={text} />
  <span
    on:click={() => {
      text !== '' && getValue(text), (text = '');
    }}>
    发送
  </span>
</div>
