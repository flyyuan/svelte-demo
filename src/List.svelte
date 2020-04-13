<script>
    export let data = [];
</script>

<div class="list">
   <div class="bottom-black-top"></div>
<!-- open each block -->
	{#each data as item}
        <div class="box">
            <div class="{item.class}">
                {item.info}
            </div>
        </div>
	{/each}
	<!-- close each block -->
    <div class="bottom-black-bottom"></div>
</div>

<style>

.bottom-black-top{
    width: 200px;
    height: 5vh;
    margin: 10px 50px;
}
.bottom-black-bottom{
    width: 200px;
    height: 7vh;
    margin: 10px 50px;
}

.box{
    overflow: auto
}

.message1 {
    float:left;
    width: auto;
    height: auto;
    margin: 3px 30px;
    background-color: skyblue;
    border-bottom-color: skyblue;
    /*为了给after伪元素自动继承*/
    color: #fff;
    font-size: 12px;
    line-height: 18px;
    padding: 5px 12px 5px 12px;
    box-sizing: border-box;
    border-radius: 6px;
    position: relative;
    word-break: break-all;
}

/** 通过对小正方形旋转45度解决 **/
.message1::before {
    content: '';
    position: absolute;
    top: 60%;
    left: -5px;
    width: 10px;
    height: 10px;
    margin-top: -10px;
    background: inherit;
    /*自动继承父元素的背景*/
    transform: rotate(45deg);
}

.message2 {
    display: flex;
    align-items: center;
    justify-content: space-around;
    float: right;
    width: auto;
    height: auto;
    margin: 10px 30px;
    background-color: #9EEA6A;
    border-bottom-color: #9EEA6A;
    /*为了给after伪元素自动继承*/
    color: #fff;
    font-size: 12px;
    line-height: 18px;
    padding: 5px 12px 5px 12px;
    box-sizing: border-box;
    border-radius: 6px;
    position: relative;
    word-break: break-all;
}


/** 通过对小正方形旋转45度解决 **/
.message2::before {
    content: '';
    position: absolute;
    top: 60%;
    right: -5px;
    width: 10px;
    height: 10px;
    margin-top: -10px;
    background: inherit;
    /*自动继承父元素的背景*/
    transform: rotate(45deg);
}
</style>