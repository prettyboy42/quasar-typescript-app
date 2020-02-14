<template>
  <q-drawer v-model="leftDrawerOpen" show-if-above bordered :width="250" :breakpoint="400">
    <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
      <div class="absolute-bottom bg-transparent">
        <q-avatar size="56px" class="q-mb-sm">
          <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
        </q-avatar>
        <div class="text-weight-bold">Tam Nguyen Duc</div>
        <div>@tamnd2</div>
      </div>
    </q-img>
    <t-menu :essentialLinks="essentialLinks"></t-menu>

    <!-- <q-list>
      <q-item-label header class="text-grey-8">Essential Links</q-item-label>
      <essential-link v-for="link in essentialLinks" :key="link.title" v-bind="link" />
    </q-list>-->
  </q-drawer>
</template>

<script lang='ts'>
import { Vue, Component, Prop } from 'vue-property-decorator';
import { getModule } from 'vuex-module-decorators';
import LayoutStoreModule from './../LayoutStoreModule';
import EssentialLink from '../../components/EssentialLink.vue';
import TMenu from '../../components/TMenu.vue';

@Component({
  components: {
    EssentialLink,
    TMenu
  }
})
export default class TheSideBarLeft extends Vue {
  store = getModule(LayoutStoreModule);
  @Prop({ default: [] }) readonly essentialLinks!: object;

  get leftDrawerOpen() {
    return this.store.leftDrawerOpen;
  }

  set leftDrawerOpen(value: boolean) {
    this.store.setLeftDrawerOpen(value);
  }
}
</script>
