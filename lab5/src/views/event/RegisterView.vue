<script setup lang="ts">
import { toRefs } from 'vue'
import { type Event } from '@/type'
import { useRouter } from 'vue-router'
import { useMessageStore } from '@/stores/message'
const props = defineProps<{
  event: Event
  id: 'String'
}>()
// eslint-disable-next-line @typescript-eslint/no-unused-vars
const { event } = toRefs(props)
const router = useRouter()
const store = useMessageStore()
const register = () => {
  // If the registration API call successful
  // Push back to the event details view
  store.updateMessage('You are successuflly registered for ' + props.event.title)
  setTimeout(() => {
  store.resetMessage()
  }, 3000)
  router.push({ name: 'event-detail-view', params: { id: props.event.id } })
}
const edit = () => {
  // If the registration API call successful
  // Push back to the event details view
  store.updateMessage('the data for ' + props.event.title + ' has been updated ')
  setTimeout(() => {
  store.resetMessage()
  }, 3000)
  router.push({ name: 'event-detail-view', params: { id: props.event.id } })
}
</script>
<template>
  <p>Register event here</p>
  <button @click="register" :style="{ backgroundColor: '#4CAF50', color: 'white' }"> Register </button> |
  <button @click="edit" :style="{ backgroundColor: '#008CBA', color: 'white' }"> Update </button>
</template>