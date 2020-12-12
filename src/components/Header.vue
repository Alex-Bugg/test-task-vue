<template>
  <header class="header">
    <div class="container">
      <div class="header_wrap">
        <img class="logo" src="@/assets/logo.png" alt="logo">
        <div class="settings">
          <ul class="settings_list">
            <li class="settings_item">
              <label>
                <span class="settings_name">font-size:</span>
                <input @change="sendSetings" v-model="settings.fontSize" class="settings_numb" type="number" value="14">
              </label>
            </li>
            <li class="settings_item">
              <label>
                <span class="settings_name">text-color:</span>
                <input @change="sendSetings" v-model="settings.color" type="color">
              </label>
            </li>
            <li class="settings_item">
              <span class="settings_name">background-color:</span>
              <input v-model="settings.backgroundColor" type="color" value="#ffffff">
            </li>
            <li class="settings_item">
              <span class="settings_name">font:</span>
              <select @change="sendSetings" v-model="settings.fontFamily">
                <option value="Arial">Arial</option>
                <option value="Helvetica">Helvetica</option>
                <option value="Verdana">Verdana</option>
                <option value="Georgia">Georgia</option>
                <option value="Andale Mono">Andale Mono</option>
                <option value="monospace">monospace</option>
                <option value="Snell Roundhand">Snell Roundhand</option>
                <option value="Impact">Impact</option>
              </select>
            </li>
            <li class="settings_item">
              <span class="settings_name">font-weight:</span>
              <select @change="sendSetings" v-model="settings.fontWeight">
                <option value="100">100</option>
                <option value="200">200</option>
                <option value="300">300</option>
                <option selected value="400">normal</option>
                <option value="500">500</option>
                <option value="600">600</option>
                <option value="700">bold</option>
                <option value="800">800</option>
                <option value="900">900</option>
              </select>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      settings: {
        fontSize: '14',
        color: 'black',
        backgroundColor: 'white',
        fontFamaly: 'Arial',
        fontWeight: 'normal'
      }
    }
  },
  methods: {
    sendSetings() {
      this.$emit('setting', this.settings)
    }
  },
}
</script>

<style lang="scss">
.header {
  background-color: #ccc;
  width: 100%;
  padding: 10px 0;
  &_wrap {
    display: flex;
    align-items: center;
  }
}

.container {
  max-width: 1440px;
  padding: 0 20px;
  margin: 0 auto;
  position: relative;
}

.logo {
  max-width: 50px;
  margin-right: 100px;
}

.settings {
  &_list{
    display: flex;
    align-items: center;
  }
  &_name {
    font-size: 20px;
  }
  &_item {
    margin-right: 5px;
  }
  &_numb {
    max-width: 30px;
  }
}
</style>