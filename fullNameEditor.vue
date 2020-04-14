<template>
  <div>
    <p>First name:<br><input v-model="firstName"></p>
    <p>Last name:<br><input v-model="lastName"></p>
  </div>
</template>

<script>
export default {
  name: 'fullNameEditor',
  data () {
    return this.getNameChunks()
  },
  props: {
    value: {
      type: String,
      required: false,
      default: ''
    }
  },
  methods: {
    getNameChunks () {
      const [firstName = '', lastName = ''] = this.value.split(' ')
      return { firstName, lastName }
    }
  },
  computed: {
    fullName () {
      return [this.firstName, this.lastName].filter(Boolean).join(' ')
    }
  },
  watch: {
    value () {
      Object.assign(this, this.getNameChunks())
    },
    fullName () {
      this.$emit('input', this.fullName)
    }
  }
}
</script>
