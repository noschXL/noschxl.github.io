<div>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <input type="checkbox" class="checkbox" id="checkbox">
  <label for="checkbox" class="checkbox-label">
    <i class="fas fa-moon moon"></i>
    <i class="fas fa-sun sun"></i>
    <span class="ball"></span>
  </label>
</div>

<style>

* {box-sizing: border-box;}

body {
  font-family: "Montserrat", sans-serif;
  background-color: #fff;
  color: #292c35;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: left;
  min-height: 100vh;
  margin: 0;
  transition: background 0.2s linear;
}

body.dark {
  background-color: #292c35;
  color: #fff;
}

.checkbox {
  opacity: 0;
  position: fixed;
  top: 1rem;
  right: 1rem;
}

.checkbox-label {
  background-color: #111;
  width: 50px;
  height: 26px;
  border-radius: 50px;
  position: fixed;
  top: 0;
  right: 0;
  padding: 5px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transform: scale(0.7);
}

.moon {color: #f1c40f;}

.sun {color: #f39c12;}

.checkbox-label .ball {
  background-color: #fff;
  width: 22px;
  height: 22px;
  position: absolute;
  left: 2px;
  top: 2px;
  border-radius: 50%;
  transition: transform 0.2s linear;
}

.checkbox:checked + .checkbox-label .ball {
  transform: translateX(24px);
}

</style>

<script>
let state = localStorage.getItem("dark");

if (state === null) {
  state = "true";
  document.body.classList.toggle("dark");
}

const isDark = state === "true";

const checkbox = document.getElementById("checkbox");
checkbox.checked = isDark;

if (isDark) {
  document.body.classList.add("dark");
}

checkbox.addEventListener("change", () => {
  localStorage.setItem("dark", checkbox.checked);
  document.body.classList.toggle("dark");
});

</script>