<template>
  <div class="home">
    <van-row type="flex" justify="center">
      <van-col span="6">
        <HomeNav></HomeNav>
      </van-col>
      <van-col span="18">
        <ShowCard title="New"></ShowCard>
      </van-col>
    </van-row>
  </div>
</template>

<script>
// @ is an alias to /src
import ShowCard from "@/components/ShowCard.vue";
import HomeNav from "@/components/HomeNav.vue";

export default {
  name: "home",
  components: { ShowCard, HomeNav }
};
</script>
