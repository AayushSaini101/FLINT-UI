<template>
  <div>
    <a-layout>
      <a-row class="navbar" type="flex" align="middle">
        <a-col :flex="5" class="logo"
          ><img src="/moja_global_logo.png" alt="moja global logo" height="40" width="57"
        /></a-col>
        <a-col :flex="3" align="middle">
          <a-row :gutter="40" justify="center" type="flex">
            <a-col>
              <a href="https://docs.moja.global/projects/flint-ui/en/latest/" target="_blank" rel="noreferrer noopener"
                >Documentation
              </a>
            </a-col>
            <a-col>
              <a href="https://github.com/moja-global/FLINT-UI" target="_blank" rel="noreferrer noopener">Github </a>
            </a-col>
            <a-col> <a href="mailto:info@moja.global" target="_blank" rel="noreferrer noopener">Contact Us </a> </a-col>
          </a-row>
        </a-col>
      </a-row>
      <a-row class="navbar navbar-mobile">
        <a-col>
          <a-row type="flex" justify="space-between">
            <a-col class="logo"
              ><img src="/moja_global_logo.png" alt="moja global logo" height="40" width="57"
            /></a-col>
            <a-col>
              <a-icon v-if="!showMenu" type="menu" @click="toggleNavbar()" />
              <a-icon v-if="showMenu" type="close" @click="toggleNavbar()" />
            </a-col>
          </a-row>
        </a-col>
        <a-col v-if="showMenu">
          <a-row class="menu-mobile">
            <a-col>
              <a href="https://docs.moja.global/projects/flint-ui/en/latest/" target="_blank" rel="noreferrer noopener"
                >Documentation
              </a>
            </a-col>
            <a-col>
              <a href="https://github.com/moja-global/FLINT-UI" target="_blank" rel="noreferrer noopener">Github </a>
            </a-col>
            <a-col> <a href="mailto:info@moja.global" target="_blank" rel="noreferrer noopener">Contact Us </a> </a-col>
          </a-row>
        </a-col>
      </a-row>
    </a-layout>
  </div>
</template>

<script>
export default {
  name: 'LandingPageNavbar',
  data() {
    return {
      showMenu: false
    }
  },
  methods: {
    toggleNavbar: function () {
      this.showMenu = !this.showMenu
    }
  }
}
</script>

<style scoped>
.navbar {
  padding: 1.2rem 1.4rem;
  background: white;
  font-size: 1.1rem;
  color: #475447;
}

.navbar a:hover {
  border-bottom: solid 2px #475447;
}

.logo {
  margin-left: 4rem;
}

.navbar-mobile {
  display: none;
}

.anticon {
  margin: 20px;
  font-size: 24px;
  cursor: pointer;
}

.menu-mobile {
  margin: 1rem 4rem;
}

.menu-mobile .ant-col {
  margin: 1rem 0;
}

@media only screen and (max-width: 768px) {
  .navbar {
    display: none;
  }
  .navbar-mobile {
    display: block;
  }
}
</style>
