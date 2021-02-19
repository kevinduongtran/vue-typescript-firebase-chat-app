<template>
  <div>
    <button class="btn btn-primary" @click="showModal">
      <b-icon icon="person-fill" class="mr-1 mb"></b-icon>Login
    </button>
    <b-modal
      id="bv-auth-modal"
      centered
      title="Sign In"
      @ok="onOk"
      @show="resetModal"
      @hidden="resetModal"
    >
      <form
        ref="email-form"
        @submit.stop.prevent="onSubmit"
        @keydown.enter="onSubmit"
      >
        <b-form-group
          label="Email"
          label-for="email-input"
          :invalid-feedback="invalidEmailFeedback"
          :state="emailValid"
        >
          <b-form-input
            id="email-input"
            v-model="email"
            required
            :state="emailValid"
          >
          </b-form-input>
        </b-form-group>
        <b-form-group
          label="Password"
          label-for="password-input"
          :invalid-feedback="invalidPasswordFeedback"
          :state="passwordValid"
        >
          <b-form-input
            id="password-input"
            type="password"
            v-model="password"
            required
            :state="passwordValid"
          >
          </b-form-input>
        </b-form-group>
      </form>
    </b-modal>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class AuthModal extends Vue {
  public invalidPasswordFeedback = "Password is required";
  public invalidEmailFeedback = "Email is required";
  public emailValid: boolean = null;
  public passwordValid: boolean = null;
  public email = "";
  public password = "";
  private reg = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

  public showModal(): void {
    this.$bvModal.show("bv-auth-modal");
  }

  hideModal(): void {
    this.$bvModal.hide("bv-auth-modal");
  }

  onOk(bvModalEvt: any): void {
    bvModalEvt.preventDefault();
    this.onSubmit();
  }

  resetModal(): void {
    this.emailValid = null;
    this.passwordValid = null;
    this.email = "";
    this.password = "";
    this.invalidPasswordFeedback = "Password is required";
    this.invalidEmailFeedback = "Email is required";
  }
  onSubmit(): void {
    console.log("enter");
    if (!this.checkFormValidity()) {
      return;
    }
    console.log(this.email, this.password);
    this.$nextTick(() => {
      this.hideModal();
    });
  }

  checkFormValidity(): boolean {
    if (this.email.length < 0) {
      this.invalidEmailFeedback = "Email is required";
    }
    if (!this.reg.test(this.email)) {
      this.invalidEmailFeedback = "Email is incorrect";
    }

    if (this.password.length < 8 && this.password.length != 0) {
      this.invalidPasswordFeedback = "Password must be 8 or more characters";
    }

    this.emailValid = this.reg.test(this.email);
    this.passwordValid = this.password.length >= 8;

    const formValid = (this.$refs["email-form"] as HTMLFormElement).checkValidity();

    return this.emailValid && this.passwordValid && formValid;
  }
}
</script>
