<template>
  <div class="container max-w-full">
    <Header />
    <section class="container max-w-full my-20 p-10">
      <h2 class="text-2xl font-semibold">Style Guide</h2>
      <div class="grid grid-cols-5 gap-4">
       <div class="input-form">
      <input-wrapper :label="label1" :placeholder="placeholder1" type="text" :show-error="showError1">
        <template #label-alt>
          <span class="label-text-alt"></span>
        </template>
      </input-wrapper>
      </div>
      <input-wrapper :label="label2" :placeholder="placeholder2" type="text" :show-error="showError2">
        <template #label-alt>
          <span class="label-text-alt"></span>
        </template>
      </input-wrapper>
    </div>
    <Textarea />
    <Select />
    <div class="btn-item mt-20">
  <Button text="Primary Button " variant="primary"  />
  <Button text="Secondary Button" variant="secondary"  />
  <Button class="btn btn-outline btn-primary mb-4 mr-5 " text="Outlined Button" variant="primary" outlined  />
  <Button class="btn btn-primary mb-4 mr-5" text="Contained Button" variant="primary" contained  />
  <Button class="btn btn-sm mb-4 mr-5" text="Small Button" size="small"  />
  <Button class="btn btn-lg mb-4 mr-5" text="Large Button" size="large" />
  <Button text="Disabled Button" disabled/>
  <Button text="Square Button" square class="mb-4" />
  <Button class="btn-success mb-4 mr-5" fab>
    <template #icon>
      <Icon iconName="check"></Icon>
    </template>
  </Button>
  <Button text="Button with Icon" class="mb-2">
    <template #icon>
      <Icon iconName="check"></Icon>
    </template>
  </Button>
  <Button class="mb-2">
    <template #icon>
      <Icon iconName="home"></Icon>
    </template>
  </Button>
</div>
<div class="Aroww icon">
          <div class="mt-8 icons flex space-x-4">
            <Icon iconName="arrow_back_ios_new"></Icon>
            <Icon iconName="arrow_forward_ios"></Icon>
            <Icon iconName="expand_less"></Icon>
            <Icon iconName="expand_more"></Icon>
          </div>
          <div class="icons">
            <div class="mt-8 icons flex space-x-4">
              <Icon iconName="home"></Icon>
              <Icon iconName="close"></Icon>
              <Icon iconName="visibility"></Icon>
              <Icon iconName="visibility_off"></Icon>
              <Icon iconName="favorite"></Icon>
              <Icon iconName="calendar_today"></Icon>
              <Icon iconName="check"></Icon>
              <Icon iconName="edit"></Icon>
              <Icon iconName="delete"></Icon>
              <Icon iconName="star"></Icon>
              <Icon iconName="star_half"></Icon>
            </div>
          </div>
        </div>
    </section>

    <section class="container max-w-full my-20 p-10">
      <h2 class="text-2xl font-semibold">Provide/Inject</h2>
 <FormLogin/>
    </section>
    <section class="container max-w-full my-10 p-5">
      <h2 class="text-2xl font-semibold">ValidateForm</h2>
      <div class="flex justify-center items-center h-screen">
  <button class="btn btn-info" @click="openModal">REGISTER FORM</button>

    <dialog id="my_modal_2" class="modal">
      <div class="modal-box">
        <div class="flex items-center justify-center">
  <span class="badge badge-lg">REGISTER FORM</span>
</div>
        <registration-form @close="closeModal"></registration-form>
      </div>
      <form method="dialog" class="modal-backdrop">
        <button @click="closeModal">close</button>
      </form>
    </dialog>
  </div>
    </section>
  </div>
  <section class="container max-w-full my-20 p-10">
      <h2 class="text-2xl font-semibold">Provide/Inject</h2>
      <LoginForm />
    </section>
</template>

<script>
import InputWrapper from './components/InputWrapper.vue';
import ThemeSwitcher from './components/ThemeSwitcher.vue';
import FormLogin from './components/Provide/FormLogin.vue';
import Header from './components/Header.vue';
import Textarea from './components/UI/Textarea.vue';
import Select from './components/UI/Select.vue';
import Button from './components/UI/Button.vue';
import Icon from './components/UI/Icons.vue';
import RegistrationForm from './components/Validation/RegistrationForm.vue';
import LoginForm from './components/Vee/LoginForm.vue';


export default {
  components: {
    InputWrapper,
    ThemeSwitcher,
    Header,
    Textarea,
    Select,
    Button,
    Icon,
    FormLogin,
    RegistrationForm,
    LoginForm,

  },

  methods: {
    toggleTheme() {
      toggleTheme();
    },
  },
  methods: {
    openModal() {
      document.getElementById('my_modal_2').showModal()
    },
    closeModal() {
      document.getElementById('my_modal_2').close()
    },
  },

  data() {
    return {
      label1: "What is your name?",
      placeholder1: "Name",
      showError1: false,
      label2: "Your password",
      placeholder2: "Password",
      showError2: false,
    };
  },
};
</script>
