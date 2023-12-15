<script setup lang="ts">
import { ref } from "vue";

const form = ref({
  email: "",
  password: "",
  remember: false,
});

function submit() {
  alert(JSON.stringify(form.value));
}
</script>

<template>
  <v-sheet width="300" class="mx-auto">
    <v-form @submit.prevent="submit">
      <v-text-field
        variant="solo"
        prepend-inner-icon="mdi-email"
        v-model="form.email"
        label="Email"
      ></v-text-field>

      <v-text-field
        type="password"
        variant="solo"
        prepend-inner-icon="mdi-key"
        v-model="form.password"
        label="Password"
      ></v-text-field>

      <v-checkbox
        v-model="form.remember"
        label="Remember Me"
        color="red-darken-1"
      ></v-checkbox>
      <v-btn type="submit" block class="mt-2" color="red-darken-1"
        >Submit</v-btn
      >
    </v-form>
  </v-sheet>
</template>
