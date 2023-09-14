<template>
    <form v-on:submit.prevent="submitForm" method="post"  id="cf-1" class="contact-form">
        <div class="form-group form-group-xs form-lg-no-space">
            <p class="input-group gutter-width-xs no-space">
                <span class="gutter-width">
                     <InputField v-model="form.name" name="cfname" type="text" placeholder="Name" :lg="false" :label="false" class-name="font-size-lg pt-0" />
                </span>

                <span class="gutter-width">
                  <InputField v-model="form.email" name="cfemail" type="email" placeholder="Email" :lg="false" :label="false" class-name="font-size-lg pt-0" />
                </span>
            </p>
        </div>

        <div class="form-group form-group-xs form-lg-no-space">
            <p class="input-group gutter-width-xs no-space">
                <span class="gutter-width">
                  <InputField v-model="form.phone" name="cfphone" type="text" placeholder="Phone no." :lg="false" :label="false" class-name="font-size-lg pt-0" />
                </span>

                <span class="gutter-width">
                  <InputField v-model="form.subject" name="subject" type="text" placeholder="Subject" :lg="false" :label="false" class-name="font-size-lg pt-0" />
                </span>
            </p>
        </div>

        <div class="form-group form-group-xs form-lg-no-space">
            <TextareaField v-model="form.message" name="message" placeholder="Message" custom-class="font-size-lg pt-0"/>
        </div>

        <div class="form-group form-group-xs">
            <button type="submit" class="btn btn-gradient">Send</button>
        </div>

        <transition appear leave-active-class="animated fadeOut">
            <div v-if="callAlert" id="alert" :class="'animated fadeIn alert alert--shadow alert-' + alertClass">
                {{ responseMessage }}
            </div>
        </transition>
    </form>
</template>

<script>
    import api from "../../mixins/api";
    import InputField from "./Fields/InputField.vue";
    import TextareaField from "./Fields/TextareaField.vue";

    export default {
      name: 'ContactsForm',
      mixins: [api],
      components: {TextareaField, InputField},
        data() {
            return {
                form: {
                    name: '',
                    email: '',
                    phone: '',
                    subject: '',
                    message: ''
                },
                successMessage: "Sender's message was sent successfully",
                warningMessage: 'Fill up the form, please!',
                errorMessage: 'Something go wrong. Try again later!',
                responseMessage: '',
                alertClass: '',
                callAlert: false
            }
        },
        methods: {
          async submitForm() {
            const requestSent = await this.post("public/store-client-container/cformitems", this.form);
            if(requestSent){
              this.form = {
                name: '',
                email: '',
                phone: '',
                subject: '',
                message: ''
              }
            }
          }
        }
    }
</script>
