<template>
  <div class="container">
  <header>
  <h1 class=text-center>Contact Us</h1>
  </header>
  <v-form ref="form" v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="firstname"
            :rules="nameRules"
            label="First name"
            filled
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="lastname"
            :rules="nameRules"
            label="Last name"
            filled
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="phonenumber"
            :rules="numberRules"
            label="Phone Number"
            filled
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            filled
            required
          ></v-text-field>
        </v-col>
            <v-col
        class="d-flex"
        cols="12"
        md="4"
      >
        <v-select
          :items="products"
          :rules="dropdownRules"
          label="Product of Interest"
          filled
        ></v-select>
      </v-col>
        <v-col
            class="d-flex"
            cols="12"
            md="4"
          >
        <v-select
          :items="about"
          :rules="dropdownRules"
          filled
          required
          label="How did you hear about us?"
        ></v-select>
      </v-col>
        <v-col
          cols="12"
          md="12"
        >
        <v-textarea
            v-model="message"
            :rules="messageRules"
            name="Message"
            label="Message"
            auto-grow
            filled
            required
        >
        </v-textarea>
        </v-col>
        <v-col
            class="d-flex"
            cols="12"
            md="4"
          >
        <v-select
          :items="location"
          :rules="dropdownRules"
          filled
          required
          label="Location"
        ></v-select>
      </v-col>

      </v-row>
      <v-btn class="success" @click="onSubmit">Submit</v-btn>
    </v-container>
  </v-form>
  </div>
</template>

<script>
  export default {
    data: () => ({
      valid: false,
      products: [
                  'Bathroom Remodeler',
                  'Deck Builder',
                  'Fence Contractor',
                  'Roof Contractor',
                  'Window Installation Service',
                  'Kitchen Remodeler',
                  'Sunroom',
                  'Patio Cover'
                ],

      dropdownRules: [
        v => !!v || 'Please make a selection'
                    ],
      about:    [
                'Online',
                'Flyer/Canvasser',
                'Phone',
                'Radio',
                'Referral',
                ],

      location: [
                "O'Fallon",
                "Lee's Summit (Kansas City)",
                'Nashville',
                'Wood Dale (Chicago)',
      ],

      firstname: '',
      lastname: '',
      nameRules: [
        v => !!v || 'Name is required'
      ],
      phonenumber: '',
      numberRules: [v => !!v || 'Phone number is required',
        v => /^\d+$/.test(v)||'Please enter a phone number'],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
      message:'',
      messageRules: [
        v => !!v || 'Message is required'
      ],
    }),
    methods: {
      onSubmit() {
        this.$refs.form.validate()
      }
    }
  }
</script>



