<script>
import { Form, Field, ErrorMessage } from 'vee-validate';
export default {
  components: {
    Form,
    Field,
    ErrorMessage,
  },
  methods: {
    onSubmit(values) {
      console.log(JSON.stringify(values, null, 2));
    },
    validateEmail(value) {
      // if the field is empty
      if (!value) {
        return 'This field is required';
      }
      // if the field is not a valid email
      const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
      if (!regex.test(value)) {
        return 'This field must be a valid email';
      }
      // All is good
      return true;
    },
  },
};
</script>

<template>
  <div>
    <Form @submit="onSubmit">
      <Field name="email" type="email" :rules="validateEmail"/><br/>
      <ErrorMessage name="email" /><br/>
      <Field name="password" type="password" /><br/>
      <button>Sign up for newsletter</button>
    </Form>
  </div>
</template>