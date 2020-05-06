<script>
  export let getVoiceValue;
  export let changeInput;
  import { onMount } from "svelte";

  let result = "";
  const recognition = new webkitSpeechRecognition();

  onMount(async () => {
    var btn = document.getElementById("voice");
    // 移动端
    btn.addEventListener("touchstart", touchstartHander, false);
    btn.addEventListener("touchend", touchendHander, false);

    // PC端
    // btn.addEventListener("mousedown", touchstartHander, false);
    // btn.addEventListener("mouseup", touchendHander, false);

    recognition.continuous = true;
    recognition.interimResults = true;
    recognition.lang = "cmn-Hans-CN";
    recognition.onresult = event => {
      if (typeof event.results !== "undefined") {
        result = event.results[0][0].transcript;
      }
    };
  });

  var touchstartHander = event => {
    recognition.start();
  };

  var touchendHander = event => {
    recognition.stop();
    getVoiceValue(result);
  };

  window.addEventListener("contextmenu", function(e) {
    e.preventDefault();
  });
</script>

<style>
  .inputVoice {
    display: flex;
    align-content: space-between;
    justify-items: center;
    padding: 4px;
    width: 100%;
    position: fixed;
    bottom: 0px;
    height: 6vh;
    background: rgb(226, 214, 214);
  }
  button {
    height: 6vh;
    margin-right: 5px;
    width: 82%;
    padding: 8px;
    font-size: 20px;
    color: #ffffff;
    background-color: #1aad19;
    box-sizing: border-box;
    text-align: center;
    text-decoration: none;
    border-radius: 5px;
    -webkit-tap-highlight-color: transparent;
    overflow: hidden;
    line-height: 4vh;
    user-select: none;
  }
  img {
    width: 40px;
    height: 40px;
    margin: 0 10px;
  }
</style>

<div class="inputVoice">
  <img
    on:click={() => {
      changeInput(0);
    }}
    alt="keyboard"
    src="./build/keyboard.png" />
  <button id="voice">按住说话</button>
</div>
