<template>
  <div style="padding: 10px">
    <h4>íëĄė</h4>
    <input placeholder="ð" />
    <div class="post-header">
      <div class="profile"></div>
      <span class="profile-name">ėŽėĐėëŠ</span>
      <span>{{ follower }}</span>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
import { onMounted, ref } from 'vue';

export default {
  setup() {
    let follower = ref([]);
    onMounted(() => {
      axios.get('/follower.json').then(res => {
        follower.value = res.data;
      });
    });
    return { follower };
  },
  data() {
    return {};
  },
};
</script>
<style lang=""></style>
