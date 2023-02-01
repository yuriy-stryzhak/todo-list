<template>
  <header class="header">
    <div class="mainer">
      <div class="header__wrap">
        <AppHeading tag="h1">Todo List</AppHeading>
        <AppButton @click="toggleForm" class="btn-show_form" :class="{ show: isShow }">+</AppButton>
      </div>
    </div>
  </header>

  <main>
    <div class="mainer">
      <transition>
        <div class="set" v-if="isShow">
          <AppInput
            @input="note.enterNote = $event.target.value"
            :value="note.enterNote"
            placeholder="Add your note..."
          />
          <AppInput
            @input="note.enterDesc = $event.target.value"
            :value="note.enterDesc"
            placeholder="Add a description..."
          />
          <AppButton @click="handleSubmit" class="set__control set__btn">Add +</AppButton>
        </div>
      </transition>

      <div class="checklist js-list"></div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue'
import AppHeading from '@/components/AppHeading.vue' // @ is an alias to /src
import AppButton from '@/components/AppButton.vue'
import AppInput from '@/components/AppInput.vue'

export default defineComponent({
  name: 'MainView',
  components: {
    AppButton,
    AppHeading,
    AppInput
  },
  // props: {
  //   value: { type: String, default: '' }
  // },
  // data() {
  //   return {
  //     note: {
  //       enterNote: '',
  //       enterDesc: ''
  //     }
  //   }
  // },
  // methods: {
  //   handleSubmit(event: Event) {
  //     event.preventDefault()
  //     console.log(this.note.enterNote, this.note.enterDesc)
  //   }
  // },
  setup() {
    const isShow = ref(false)

    const toggleForm = () => {
      isShow.value = !isShow.value
    }

    const note = reactive({
      enterNote: '',
      enterDesc: ''
    })

    const handleSubmit = () => {
      console.log(note.enterNote, note.enterDesc)
      note.enterNote = ''
      note.enterDesc = ''
    }

    return {
      isShow,
      toggleForm,
      note,
      handleSubmit
    }
  }
})
</script>

<style>
.mainer {
  max-width: 1140px;
  padding: 0 15px;
  margin: 0 auto;
}

header {
  background-color: var(--lamppost);
  text-align: center;
  padding: 25px 0;
  color: var(--coral);
  margin-bottom: 42px;
  border-bottom: 1px solid rgba(195, 195, 195, 0.4);
  position: relative;
  z-index: 2;
}

.header__wrap {
  position: relative;
}

.btn-show_form {
  position: absolute;
  right: 0;
  top: 50%;
  padding: 0;
  text-align: center;
  font-size: 50px;
  line-height: 0;
  transform: translateY(-50%);
  width: 45px;
  height: 45px;
  color: var(--coral);
  transition: all 0.25s;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-tap-highlight-color: transparent;
}

.btn-show_form.show {
  transform: translateY(-50%) rotate(45deg);
}

.set {
  background-color: #88839e;
  padding: 12px 15px;
  gap: 15px;
  flex-wrap: wrap;
  display: flex;
}

.v-enter-from,
.v-leave-to {
  transform: translateY(-100%);
  opacity: 0;
  visibility: hidden;
}

.v-enter-active,
.v-leave-active {
  transition: all 0.25s;
}

.v-enter-to,
.v-leave-from {
  transform: none;
  opacity: 1;
  visibility: visible;
}

.set__btn {
  flex-grow: 1;
  cursor: pointer;
  background-color: var(--greeny);
  color: #fff;
  transition: all 0.25s;
  font-size: 24px;
}

.set__btn:hover {
  transform: scale(0.98);
}
</style>
