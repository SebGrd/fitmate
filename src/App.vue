<template>
  <div id="app">
    <el-container style="height: 100vh;">
      <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
        <el-menu :default-openeds="['1']">
          <el-submenu index="1">
            <template slot="title"><i class="el-icon-house"></i>My gym</template>
            <el-menu-item index="1-1">Gym (planning & stuf)</el-menu-item>
            <el-menu-item index="1-2">My workouts</el-menu-item>
            <el-menu-item index="1-3">Stats (body heatmap)</el-menu-item>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title"><i class="el-icon-menu"></i>Exercices</template>
            <el-menu-item-group>
              <template slot="title">Group 1</template>
              <el-menu-item index="2-1">Option 1</el-menu-item>
              <el-menu-item index="2-2">Option 2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="Group 2">
              <el-menu-item index="2-3">Option 3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="2-4">
              <template slot="title">Option 4</template>
              <el-menu-item index="2-4-1">Option 4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
        </el-menu>
      </el-aside>

      <el-container>
        <el-header style="text-align: right; font-size: 12px">
          <el-dropdown>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>View</el-dropdown-item>
              <el-dropdown-item>Add</el-dropdown-item>
              <el-dropdown-item>Delete</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <span>Tom</span>
        </el-header>

        <el-main>
          <body-selector ref="bodySelector" :selected.sync="selectedParts"/>
          <body-parts-list :selected="selectedParts" @select-part="selectPart"/>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>

import BodySelector from "@/components/bodySelector/BodySelector";
import BodyPartsList from "@/components/bodySelector/BodyPartsList";
export default {
  name: 'app',
  components: {BodyPartsList, BodySelector},
  data() {
    return {
      selectedParts: [],
    };
  },
  methods: {
    selectPart(part) {
      this.$refs.bodySelector.partClick(part);
    },
  },
}
</script>

<style>
body{
  margin: 0;
  box-sizing: border-box;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.flex{
  display: flex;
}
</style>
