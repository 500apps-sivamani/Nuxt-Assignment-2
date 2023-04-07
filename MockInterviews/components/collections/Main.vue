<template>
  <CollectionsList
    :getTemplateData="getTemplateData"
    @is_sidebar="openSidebar"
  />
  <div v-if="is_sidebar" :key="render">
    <CollectionsAdd @postDatabody="postData" />
  </div>
</template>
<script setup lang="ts">
const is_sidebar = ref(false);
const render = ref(0);

//GET Call
const getOptions = {
  method: "GET",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiNmZlZDJiYTgwYThkNGM0MjlhZGZiOGQ1ZTZmZTY0ODAiLCJkIjoiMTY4MDA4NCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzk3Mjl9.5cJkrudAvTWoVRigTNcfQ321W_lOyMm-xsb9rMxuVBE`,
  },
};
let getData = useAuthLazyFetch(
  "https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  getOptions
);

let getTemplateData = ref(getData.data._rawValue);

//POST Call
const postData = async (body: Object) => {
  const options = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiNmZlZDJiYTgwYThkNGM0MjlhZGZiOGQ1ZTZmZTY0ODAiLCJkIjoiMTY4MDA4NCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzk3Mjl9.5cJkrudAvTWoVRigTNcfQ321W_lOyMm-xsb9rMxuVBE`,
    },
    body: JSON.stringify(body),
  };
  await useAuthLazyFetchPost(
    "https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/",
    options
  );
  getTemplateData.value.unshift(body);
  is_sidebar.value = false;
};

const openSidebar = () => {
  is_sidebar.value = true;
  render.value++;
};
</script>
