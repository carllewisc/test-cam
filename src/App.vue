<template>
  <div class="bg-gray-200 h-screen">
    <form-dni class="flex items-center h-full" />
  </div>
</template>

<script>

import FormDni from "./components/FormDni";

export default {
  name: 'App',
  components: {
    FormDni
  }
}
</script>

<style>
.d-contents {
  display: contents;
}
</style>
