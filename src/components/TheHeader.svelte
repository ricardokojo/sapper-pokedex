<style>
.semiCircle {
  position: relative;
  background: rgb(128,9,9);
  background: linear-gradient(150deg, rgba(128,9,9,1) 0%, rgba(255,17,17,1) 50%, rgba(255,17,17,1) 100%);
  height: 20vh;

  border-bottom: 2rem solid #333;
  box-shadow: 0 0 1rem .1rem #333;
}

.semiCircle::before {
  position: absolute;
  content: '';
  left: 50%;
  z-index: 10;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: #fefefe;
  transform: translateX(-50%) translateY(50%);
  bottom: 0px;

  border: 2rem solid #333;
  box-shadow: 0 0 1rem .1rem #333;
}
</style>

<header class="semiCircle">
</header>
