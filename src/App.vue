<template>
  <div id="app">
    <Header></Header>
    <Banner></Banner>  
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Banner from './components/Banner.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Header,
    Banner
  }
}
</script>

<style lang="scss">
//Font
@import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');

//Variables
$primary-color: #1D5297;
$secondary-color: #FF6A17;
$black-gray-color: #333333;
$green-color: #51C99C;

//Grid System
//----- Extends
%clearfix:after {
	display:block;
	clear:both;
	content:'';
}

.container {
  margin: 0 auto;
  padding: 1rem;
  position: relative;
  @media (min-width: 768px){
    width: 750px;
  }
  @media (min-width: 992px){
    width: 970px;
  }
  @media (min-width: 1200px){
    width: 1170px;
  }
}

//----- Grid System
$grid-spacing:3%;

.row {
	@extend %clearfix;

	& + & {
		margin-top:$grid-spacing;
	}
}

[class^="col-"] {
	float:left;
	margin-right:$grid-spacing;
	-webkit-box-sizing:border-box;
	-moz-box-sizing:border-box;
	box-sizing:border-box;

	&:last-child {
		margin-right:0%;
	}
}

//----- Columns (Manual)
/*
.col-1 { width:5.583333333333333%; }
.col-2 { width:14.16666666666667%; }
.col-3 { width:22.75%; }
.col-4 { width:31.33333333333333%; }
.col-5 { width:39.91666666666667%; }
.col-6 { width:48.5%; }
.col-7 { width:57.08333333333333%; }
.col-8 { width:65.66666666666666%; }
.col-9 { width:74.25%; }
.col-10 { width:82.83333333333333%; }
.col-11 { width:91.41666666666666%; }
.col-12 { width:100%; }
*/

//----- Columns (Automatic)
.col-1 { width:(100% / 12) - ($grid-spacing * 11 / 12); }
.col-2 { width:(100% / 6) - ($grid-spacing * 10 / 12); }
.col-3 { width:(100% / 4) - ($grid-spacing * 9 / 12); }
.col-4 { width:(100% / 3) - ($grid-spacing * 8 / 12); }
.col-5 { width:(100% / 2.4) - ($grid-spacing * 7 / 12); }
.col-6 { width:(100% / 2) - ($grid-spacing * 6 / 12); }
.col-7 { width:(100% / 1.714285714285714) - ($grid-spacing * 5 / 12); }
.col-8 { width:(100% / 1.5) - ($grid-spacing * 4 / 12); }
.col-9 { width:(100% / 1.333333333333333) - ($grid-spacing * 3 / 12); }
.col-10 { width:(100% / 1.2) - ($grid-spacing * 2 / 12); }
.col-11 { width:(100% / 1.090909090909091) - ($grid-spacing * 1 / 12); }
.col-12 { width:100%; }

//General
body {
  margin: 0;
  font-size: 16px;
  background: scale-color($primary-color, $lightness: 95%);
}
#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $black-gray-color;
}
</style>
