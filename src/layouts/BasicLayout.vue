<template>
  <van-nav-bar
    title="Title"
    left-text="Back"
    left-arrow
    @click-left="onClickLeft"
    @click-right="onClickRight"
  >
    <template #right>
      <van-icon
        name="search"
        size="18"
      />
    </template>
  </van-nav-bar>

  <van-tabbar
    v-model="active"
    @change="onChange"
  >
    <van-tabbar-item
      icon="home-o"
      name="home"
      >home</van-tabbar-item
    >
    <van-tabbar-item
      icon="search"
      name="team"
      >team</van-tabbar-item
    >
    <van-tabbar-item
      icon="friends-o"
      name="user"
      >user</van-tabbar-item
    >
  </van-tabbar>

  <div id="content">
    <template v-if="active === 'home'"><Home /> </template>
    <template v-if="active === 'team'"><Team /> </template>
    <template v-if="active === 'user'"><User /> </template>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Home from '../pages/Home.vue';
import Team from '../pages/Team.vue';
import User from '../pages/User.vue';

const onClickLeft = () => alert('back');
const onClickRight = () => alert('search');

const active = ref('home');
const onChange = (index) => showToast(`Tab ${index}`);
</script>
