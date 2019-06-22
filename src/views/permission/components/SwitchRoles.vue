<template>
  <div>
    <div style="margin-bottom:15px;">
      Your roles: {{ roles }}
    </div>
    Switch roles:
    <el-radio-group v-model="switchRoles">
      <el-radio-button label="editor" />
      <el-radio-button label="maoyali" />
      <el-radio-button label="admin" />
    </el-radio-group>
  </div>
</template>

<script>
export default {
  computed: {
    roles() {
      return this.$store.getters.roles
    },
    switchRoles: {
      get() {
        debugger
        return this.roles[0]
      },
      set(val) {
        debugger

        this.$store.dispatch('user/changeRoles', val).then(() => {
        debugger

          this.$emit('change')
        })
      }
    }
  }
}
</script>
