<template>
  <div class="main-container">
    <h2 class="search-header">Search Records</h2>
    <input type="text" placeholder="Enter Employee Name" class="employee-searchbar"/>
    <button class="search-employee-btn">Search</button>
  </div>
</template>

<style scoped>
.main-container {
  min-height: calc(100vh - 74px);
  height: fit-content;
  padding: 3rem 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  background: url('../assets/hexagonBg.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  background-attachment: fixed;
}

.search-header {
  color: var(--color-white);
}

.employee-searchbar {
  width: 70rem;
  min-width: 29rem;
  margin-top: 2rem;
  padding: 1.5rem 1.5rem;
  font-size: 1.5rem;
  box-sizing: border-box;
  outline: none;
  border: none;
  border-radius: 8px;
  font-family: 'Comfortaa';
}

.search-employee-btn {
  font-size: large;
  width: 300px;
  padding: 1rem 0;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 2.5rem;
}

.search-employee-btn:active {
  color: var(--color-white);
  background-color: var(--color-pink1);
}

@media only screen and (max-width:720px){
  .employee-searchbar {
    width: 50rem;
  }
}

@media only screen and (max-width:520px){
  .employee-searchbar {
    width: 30rem;
  }
}
</style>
