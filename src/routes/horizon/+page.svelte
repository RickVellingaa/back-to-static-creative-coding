<section>
    <div class="moon"/>
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
  background: linear-gradient(
    to top,
    #283e51,
    #0a2342
  );
}

.moon{
  background-color: #a2a2a2cf;
  position:absolute;
  filter: blur(2px);
  /*padding: 10px;*/
  left: 3em;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  box-shadow: 5px 0 10px 3px rgba(229,229,229,0.3),
              0 0 10px 2px rgba(229,229,229,0.3),
              5px 0 50px 10px rgba(229,229,229,0.3),
               0px 0 3px 2px rgba(229,229,229,0.3);
  top: 3em;
  margin: auto;
  
}

.moon::after{
  content: "";
  background-color: #a2a2a2cf;
  display: block;
  position: absolute;
  left:  75px;
  top:  30px;
  width: 35px;  
  height: 35px;
  border-radius:50%;
  box-shadow: 3px 0 0 1px rgba(98, 98, 98, 0.51),
              7px 45px 0 -5px rgba(162, 162, 162, 0.9),
              9px 45px 0 -5px rgba(100, 100, 100, 0.51),
              35px 20px 0 -10px rgba(162, 162, 162, 0.9),
               37px 20px 0 -10px rgba(100, 100, 100, 0.51);
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
	background: linear-gradient(
    to top,
    #F1F6F9,
    #C3D6DC
  );
	transform: skew(-20deg);
	border-top-right-radius: 100%;
	z-index: 2;
  filter: blur(1px);
}

.mountain2 {
	position: absolute;
	right: -10%;
	bottom: 0;
  filter: blur(1px);
	width: 55vw;
	height: 35vh;
	background: linear-gradient(
    to bottom,
    #F1F6F9,
    #C3D6DC
  );
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