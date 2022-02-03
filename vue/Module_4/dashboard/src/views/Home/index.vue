<template>
  <div>
    <custom-header @create-account="handleAccountCreate" @login="handleLogin" />
    <contact />
    <div class="flex justify-center py-10 bg-brand-gray">
      <p class="font-medium text-center text-gray-800">
        Feedbacker &copy; {{ new Date().getFullYear() }}
      </p>
    </div>
  </div>
</template>

<script>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import CustomHeader from './CustomHeader.vue'
import Contact from './Contact.vue'
import useModal from '../../hooks/useModal'

export default {
  components: { CustomHeader, Contact },
  setup () {
    const router = useRouter()
    const modal = useModal()

    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedbacks' })
      }
    })

    function handleLogin () {
      modal.open({
        component: 'ModalLogin'
      })
    }

    return {
      handleLogin
    }
  }
}
</script>
