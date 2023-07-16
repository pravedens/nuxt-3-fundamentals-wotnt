<script lang="ts" setup>
const route = useRoute();

// {"Response":"False","Error":"Incorrect IMDb ID."}

const { data, error } = await useFetch(
  `https://www.omdbapi.com/?apikey=8e3f600b&i=${route.params.id}`,
  {
    pick: ["Plot", "Title", "Error"],
    key: `/movies/${route.params.id}`,
  }
);
if (error.value) {
  // handle accordingly
}
if (data.value.Error === "Incorrect IMDb ID.") {
  showError({ statusCode: 404, statusMessage: "Page Not Found" });
}
</script>

<template>
  <div>
    <pre>
        {{ data }}
    </pre>
  </div>
</template>

<style scoped></style>
