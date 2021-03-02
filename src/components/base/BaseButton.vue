<template>
  <button>
    <slot></slot>
  </button>
</template>

<style scoped>
button {
  background-color: #36C2E9;
  border: 1px solid #1493b6;
  color: white;
  padding: 0.8rem;
  text-align: center;
  border-radius: 4px;
  transition-duration: 0.4s;
}

button:hover {
  cursor: pointer;
  background-color: white;
  color: #36C2E9;
}
</style>