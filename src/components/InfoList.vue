<template>
  <div class="info-list-wrapper">
    <div
      class="long-info-list list-item"
      v-for="(item, index) in longInfoList"
      :key="index"
    >

    <font-awesome-icon class="icon" :icon="item.icon" />
      {{ item.msg }}
    </div>
    <div class="short-list-wrapper">
      <div
        class="short-info-list list-item"
        v-for="(item, index) in shortInfoList"
        :key="index"
      >
        <font-awesome-icon class="icon" :icon="item.icon" />
        {{ item.msg }}
      </div>
    </div>
    <div class="icons">
      <div class="icon" v-for="(item, index) in icons" :key="index">
        <font-awesome-icon
        @mouseenter="() => setColor(item)"
        @mouseleave="() => resetColor(item)"
        :style="{color: item.hovTheme, backgroundColor: item.bgC}" class="icon" :icon="item.icon" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { State, Getter, Action, Mutation, namespace } from "vuex-class";

@Component
export default class extends Vue {
  created() {}
  @Getter("words") words: any;
  @State("dictionary") dictionary: any;

  get longInfoList() {
    return [
      {
        icon: ["fas", "home"],
        msg: this.words.address1,
      },
      {
        icon: ["fas", "home"],
        msg: this.words.address2,
      },
    ];
  }

  get shortInfoList() {
    return [
      {
        icon: ["fas", "envelope"],
        msg: this.words.email,
      },
      {
        icon: ["fas", "phone-alt"],
        msg: this.words.phone,
      },
      {
        icon: ["fas", "tv"],
        msg: this.words.web,
      },
    ];
  }

  setColor(item:any) {
    item.hovTheme = item.theme;
    if(item.hovTheme === '#fff') {
      item.bgC = '#000';
    }
  }

  resetColor(item:any) {
    item.hovTheme = '#000';
    item.bgC = '#fff';
  }

  icons = [
    {
      hovTheme: '#000',
      icon:　['fab', 'facebook-square'],
      theme: 'rgb(59, 87, 157)',
    },
    {
      hovTheme: '#000',
      icon:　['fab', 'github-square'],
      theme: '#fff',
      bgC: '#fff',
    },
    {
      hovTheme: '#000',
      icon:　['fab', 'linkedin'],
      theme: 'rgb(24, 119, 242)',
    },
    {
      hovTheme: '#000',
      icon:　['fab', 'twitter-square'],
      theme: 'rgb(59, 200, 244)',
    },
  ]
}
</script>

<style lang="scss" scoped>
  .info-list-wrapper{
    width: 1160px;
    margin: 0 auto;
    margin-top: 36px;
  }

  .list-item{
    padding: 6px 0;
  }

  .short-list-wrapper{
    float: left;
    overflow: hidden;
    margin-right: 24px;
  }

  .icons {
    display: flex;
    float: right;
    margin-top: 40px;

    .icon{
      cursor: pointer;
      width: 50px;
      height: 50px;
      margin: 0 5px;
      transition: all ease .3s;
    }
  }
</style>
