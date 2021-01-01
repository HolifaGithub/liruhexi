<template>
<div class="container">
	<div class="audio-container">
		<p class="music-title">{{isShowTitle ? `正在为您播放：&lt;&lt;易烊千玺 - 大城小爱 (Live)&gt;&gt;...` : `点击播放歌曲~~`}}</p>
		<audio :src="musicSrc" :autoplay="true" :loop="true" id="audio" controls class="audio" @play="onClick" @pause="onClick"/>
	</div>
      <div class="box">
        <ul class="minbox">
            <li v-for="item in insetPics" :key="item">
				<img  :src="item"/>
			</li>
        </ul>
        <ol class="maxbox">
              <li v-for="item in insetPics" :key="item">
				<img  :src="item"/>
			</li>
        </ol>
    </div>
</div>
</template>

<script>
import {baseSrc} from '../constant'
import { reactive,ref } from 'vue'
export default {
  name:"App",
  setup(){
	  const { musicSrc, isShowTitle, onClick } = useMusic();
	  const { insetPics , outsetPics } = usePictures();
	  return { musicSrc,isShowTitle, onClick, insetPics, outsetPics }
  }
}

const useMusic = ()=>{
	const musicSrc = `${baseSrc}%E6%98%93%E7%83%8A%E5%8D%83%E7%8E%BA%20-%20%E5%A4%A7%E5%9F%8E%E5%B0%8F%E7%88%B1%20%28Live%29.mp3`
	let isShowTitle = ref(false);
	const onClick = ()=>{
		console.log('aa');
		isShowTitle.value = !isShowTitle.value;
	}
	return { musicSrc, isShowTitle, onClick }
}

const usePictures = ()=>{
	const pic1 = `${baseSrc}1.jpg`
	const pic2 = `${baseSrc}2.jpg`
	const arr = [pic1,pic2];
	const insetPics = reactive(arr.concat(arr,arr));
	const outsetPics = reactive(arr.concat(arr,arr));
	return { insetPics , outsetPics }
}
</script>

<style scoped>
.container{
	width:100%;
	height: 35rem;
	padding-top: 2rem;
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	align-items: center;
	background-image: linear-gradient(to right, pink 0%, skyblue 100%);
}
.audio{
	margin-left: 1rem;
}
.audio-container{
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: flex-start;
}
.music-title{
	color: #fff;
	margin-bottom: 1rem;
	font-size: 1rem;
	width:100%;
	text-align: center;
	height: 30px;
	background-color: rgba(255,255,255,0.3);
	border-radius: 5px;
	line-height: 30px;
	border-radius: 1px;
	pointer-events: none;
}
.box {
	width:200px;
	height:200px;
	margin-top: 50px;
	user-select: none;
	background-size:cover;
	background-repeat:no-repeat;
	background-attachment:fixed;
	background-size:100% 100%;
	-webkit-transform-style:preserve-3d;
	-webkit-transform:rotateX(13deg);
	-webkit-animation:move 5s linear infinite;
}
.minbox {
	width:100px;
	height:100px;
	position:absolute;
	left:50px;
	top:30px;
	-webkit-transform-style:preserve-3d;
}
.minbox li {
	width:100px;
	height:100px;
	position:absolute;
	left:0;
	top:0;
}
.minbox li:nth-child(1) {
	/*background:url(../img/01.png) no-repeat 0 0;
	*/
    -webkit-transform:translateZ(50px);
}
.minbox li:nth-child(1) img, .minbox li:nth-child(2) img, .minbox li:nth-child(3) img, .minbox li:nth-child(4) img, .minbox li:nth-child(5) img, .minbox li:nth-child(6) img {
	width:100%;
	height:100%;
}
.minbox li:nth-child(2) {
	/*background:url(../img/02.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateX(180deg) translateZ(50px);
}
.minbox li:nth-child(3) {
	/*background:url(../img/03.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateX(-90deg) translateZ(50px);
}
.minbox li:nth-child(4) {
	/*background:url(../img/04.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateX(90deg) translateZ(50px);
}
.minbox li:nth-child(5) {
	/*background:url(../img/05.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateY(-90deg) translateZ(50px);
}
.minbox li:nth-child(6) {
	/*background:url(../img/06.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateY(90deg) translateZ(50px);
}
.maxbox li:nth-child(1) {
	/*background:url(../img/1.png) no-repeat 0 0;
	*/
    -webkit-transform:translateZ(50px);
}
.maxbox li:nth-child(2) {
	/*background:url(../img/2.png) no-repeat 0 0;
	*/
    -webkit-transform:translateZ(50px);
}
.maxbox li:nth-child(3) {
	/*background:url(../img/3.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateX(-90deg) translateZ(50px);
}
.maxbox li:nth-child(4) {
	/*background:url(../img/4.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateX(90deg) translateZ(50px);
}
.maxbox li:nth-child(5) {
	/*background:url(../img/5.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateY(-90deg) translateZ(50px);
}
.maxbox li:nth-child(6) {
	/*background:url(../img/6.png) no-repeat 0 0;
	*/
    -webkit-transform:rotateY(90deg) translateZ(50px);
}
.maxbox {
	width:300px;
	height:200px;
	position:absolute;
	left:0;
	top:-20px;
	-webkit-transform-style:preserve-3d;
}
.maxbox li {
	width:200px;
	height:200px;
	background:#fff;
	border:1px solid #ccc;
	position:absolute;
	left:0;
	top:0;
	opacity:0.2;
	-webkit-transition:all 1s ease;
}
.maxbox li:nth-child(1) {
	-webkit-transform:translateZ(100px);
}
.maxbox li:nth-child(1) img, .maxbox li:nth-child(2) img, .maxbox li:nth-child(3) img, .maxbox li:nth-child(4) img, .maxbox li:nth-child(5) img, .maxbox li:nth-child(6) img {
	width:100%;
	height:100%;
}
.maxbox li:nth-child(2) {
	-webkit-transform:rotateX(180deg) translateZ(100px);
}
.maxbox li:nth-child(3) {
	-webkit-transform:rotateX(-90deg) translateZ(100px);
}
.maxbox li:nth-child(4) {
	-webkit-transform:rotateX(90deg) translateZ(100px);
}
.maxbox li:nth-child(5) {
	-webkit-transform:rotateY(-90deg) translateZ(100px);
}
.maxbox li:nth-child(6) {
	-webkit-transform:rotateY(90deg) translateZ(100px);
}
.box:hover ol li:nth-child(1) {
	-webkit-transform:translateZ(300px);
	width:300px;
	height:300px;
	opacity:0.8;
	left:-100px;
	top:-100px;
}
.box:hover ol li:nth-child(2) {
	-webkit-transform:rotateX(180deg) translateZ(300px);
	width:300px;
	height:300px;
	opacity:0.8;
	left:-100px;
	top:-100px;
}
.box:hover ol li:nth-child(3) {
	-webkit-transform:rotateX(-90deg) translateZ(300px);
	width:300px;
	height:300px;
	opacity:0.8;
	left:-100px;
	top:-100px;
}
.box:hover ol li:nth-child(4) {
	-webkit-transform:rotateX(90deg) translateZ(300px);
	width:300px;
	height:300px;
	opacity:0.8;
	left:-100px;
	top:-100px;
}
.box:hover ol li:nth-child(5) {
	-webkit-transform:rotateY(-90deg) translateZ(300px);
	width:300px;
	height:300px;
	opacity:0.8;
	left:-100px;
	top:-100px;
}
.box:hover ol li:nth-child(6) {
	-webkit-transform:rotateY(90deg) translateZ(300px);
	width:300px;
	height:300px;
	opacity:0.8;
	left:-100px;
	top:-100px;
}
@keyframes move {
	0% {
	-webkit-transform:rotateX(13deg) rotateY(0deg);
}
100% {
	-webkit-transform:rotateX(13deg) rotateY(360deg);
}
}
</style>
