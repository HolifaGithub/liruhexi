<template>
  <div class="container">
    <div class="title">例如河西合集</div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.container{
    width:100%;
	height: 100px;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	background-image: linear-gradient(to right, pink 0%, skyblue 100%);
}
.container .title{
    color: #eee;
	font-size: 3rem;
	text-shadow: 5px 5px 5px black, 0px 0px 2px pink; 
}
</style>