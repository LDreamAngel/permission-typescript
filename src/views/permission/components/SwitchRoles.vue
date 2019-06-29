<template>
  <div>
    <div style="margin-bottom:15px;">
      <!-- {{ $t('permission.roles') }}： {{ roles }} -->
      角色： {{ roles }}
    </div>
    <!-- {{ $t('permission.switchRoles') }}： -->
    选择角色：
    <el-radio-group v-model="switchRoles">
      <el-radio-button label="editor" />
      <el-radio-button label="admin" />
    </el-radio-group>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { UserModule } from '@/store/modules/user'

@Component({
  name: 'SwitchRoles'
})
export default class extends Vue {
  get roles() {
    return UserModule.roles
  }

  get switchRoles() {
    return this.roles[0]
  }

  set switchRoles(value) {
    UserModule.ChangeRoles(value).then(() => {
      this.$emit('change')
    })
  }
}
</script>
