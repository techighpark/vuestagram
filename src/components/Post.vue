<template lang="">
  <div class="post">
    <div class="post-header">
      <div class="profile" :style="profileCssObject"></div>
      <span class="profile-name">{{ post.name }}</span>
    </div>
    <div
      @click="$store.commit('toggleLike')"
      :class="post.filter"
      class="post-body"
      :style="postCssObject"
    ></div>
    <div class="post-content">
      <p>
        {{ $store.state.likes }}
        {{ $store.state.likes === 1 ? 'Like' : 'Likes' }}
      </p>
      <p>
        <strong>{{ post.name }}</strong> {{ post.content }}
      </p>
      <p class="date">{{ post.date }}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'post',
  props: {
    post: Object,
  },
  data() {
    return {
      profileCssObject: { backgroundImage: `url(${this.post.userImage})` },
      postCssObject: { backgroundImage: `url(${this.post.postImage})` },
    };
  },
};
</script>
<style>
.post {
  width: 100%;
}
.profile {
  width: 30px;
  height: 30px;
  background-size: 100%;
  border-radius: 50%;
  float: left;
}
.profile-name {
  display: block;
  float: left;
  padding-left: 10px;
  padding-top: 7px;
  font-size: 14px;
}
.post-header {
  height: 30px;
  padding: 10px;
}
.post-body {
  height: 450px;
  background-position: center;
  background-size: cover;
}
.post-content {
  padding-left: 15px;
  padding-right: 15px;
  font-size: 14px;
}
.date {
  font-size: 11px;
  color: grey;
  margin-top: -8px;
}
</style>
