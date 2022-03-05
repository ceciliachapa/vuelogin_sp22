<script setup></script>

<script setup>
import userAuth from "../composable/useAuth";
const { isAuthenticated, user } = userAuth();
</script>

<template>
  <div
    class="
      flex flex-col
      items-center
      justify-center
      space-y-12
      min-h-screen-nonav
    "
  >
    <h2
      v-if="!isAuthenticated"
      class="text-6xl tracking-tighter font-bold text-purple-900 font-serif"
    >
      <p>Welcome</p>
      <hr />
      <img src="../assets/welcome.png" alt="Hello" />
    </h2>

    <h2
      v-else
      class="text-6xl tracking-tighter font-bold text-purple-900 font-sans"
    >
      <h2 class="justify-center">
        <p>Welcome {{ user }}</p>
      </h2>
      <br />
      <img src="../assets/welcome.png" alt="Hello" />
    </h2>
  </div>
</template> 