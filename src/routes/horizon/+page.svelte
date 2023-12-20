<section>
    <div class="sun"/>
    <div class="snow"/>

    <div class="mountain1"/>
    <div class="mountain2"/>
</section>

<style>
section {
    position: absolute;
    left: 0;
    bottom: 0;
	width: 100%;
	height: calc(100vh - 90px);
	color: black;
	background-color: rgb(178, 221, 226);
}

.sun {
    width: 100px;
    height: 100px;
    filter: blur(5px);
    margin: 2em;
    border-radius: 50%;
    background-color: rgb(237, 187, 36);
    position: absolute;
}

.snow, .snow:before, .snow:after {
  position: absolute;
  top: -650px;
  left: 0;
  bottom: 0;
  right: 0;
  background-image: 
  radial-gradient(4px 4px at 100px 50px, #fff , transparent), 
  radial-gradient(6px 6px at 200px 150px, #fff, transparent), 
  radial-gradient(3px 3px at 300px 250px, #fff 50%, transparent), 
  radial-gradient(4px 4px at 400px 350px, #fff 50%, transparent), 
  radial-gradient(6px 6px at 500px 100px, #fff 50%, transparent);
  background-size: 650px 650px;
  background-repeat: repeat;
  animation: snow 3s linear infinite;
  content: "";
}

.snow:after {
  margin-left: -250px;
  opacity: 0.5;
  filter: blur(2px);
  animation-duration: 6s;
  animation-direction: reverse;
}

.snow:before {
  margin-left: -350px;
  opacity: 0.7;
  filter: blur(1px);
  animation-duration: 9s;
  animation-direction: reverse;
}

.mountain1 {
	position: absolute;
	bottom: -5%;
	left: -10%;
	width: 85vw;
	height: 35vh;
	background-color: red;
	transform: skew(-20deg);
	border-top-right-radius: 100%;
	z-index: 2;
}

.mountain2 {
	position: absolute;
	right: -10%;
	bottom: 0;
	width: 55vw;
	height: 35vh;
	background-color: pink;
	z-index: 1;
	border-top-left-radius: 100%;
	transform: skew(20deg);
}

@keyframes snow {
  to {
    transform: translateY(650px);
  }
}

</style>