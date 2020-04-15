<template>
  <div>
    <p>{{ fullName }}</p>
    <p>Full name:<br><input v-model="fullName" /></p>
    <FullNameEditor v-model="fullName" />
  </div>
</template>

<script>
import FullNameEditor from './fullNameEditor'

export default {
  components: { FullNameEditor },
  data () {
    return {
      fullName: 'John Doe'
    }
  }
}
</script>
