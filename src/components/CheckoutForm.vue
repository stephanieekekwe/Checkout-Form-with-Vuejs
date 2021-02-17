<template>
  <div id="checkout-form">
    <h4 class="mb-3">Billing address</h4>
    <form class="needs-validation" v-on:submit.prevent="submit">
      <div class="row">
        <div class="col-md-6 mb-3">
          <label for="firstName">
            First name
            <span class="text-danger">*</span>
          </label>
          <input
            v-model="$v.first_name.$model"
            type="text"
            class="form-control"
            :class="{'is-invalid': validationStatus($v.first_name)}"
            id="firstName"
            placeholder
            value
            required
          />
          <div v-if="!$v.first_name.required" class="invalid-feedback">Valid first name is required.</div>
        </div>
        <div class="col-md-6 mb-3">
          <label for="lastName">
            Last name
            <span class="text-danger">*</span>
          </label>
          <input
            v-model="$v.last_name.$model"
            type="text"
            class="form-control"
            :class="{'is-invalid': validationStatus($v.last_name)}"
            id="lastName"
            placeholder
            value
            required
          />
          <div v-if="!$v.last_name.required" class="invalid-feedback">Valid last name is required.</div>
        </div>
      </div>

      <div class="mb-3">
        <label for="email">
          Email
          <span class="text-danger">*</span>
        </label>
        <input
          v-model="$v.email.$model"
          type="email"
          class="form-control"
          :class="{'is-invalid': validationStatus($v.email)}"
          id="email"
          placeholder="you@example.com"
        />
        <div
          v-if="!$v.email.required"
          class="invalid-feedback"
        >Please enter a valid email address for shipping updates.</div>
      </div>

      <div class="mb-3">
        <label for="phone">
          Phone Number
          <span class="text-danger">*</span>
        </label>
        <input
          v-model.number="$v.phone.$model"
          type="number"
          class="form-control"
          :class="{'is-invalid': validationStatus($v.phone)}"
          id="phonenumber"
          placeholder
        />
        <div
          v-if="!$v.phone.required"
          class="invalid-feedback"
        >Please enter a valid Phone Number for shipping updates.</div>
      </div>

      <div class="mb-3">
        <label for="address">
          Address
          <span class="text-danger">*</span>
        </label>
        <input
          v-model="$v.address_1.$model"
          type="text"
          class="form-control"
          :class="{'is-invalid': validationStatus($v.address_1)}"
          id="address"
          placeholder="1234 Main St"
          required
        />
        <div
          v-if="!$v.address_1.required"
          class="invalid-feedback"
        >Please enter your shipping address.</div>
      </div>

      <div class="mb-3">
        <label for="address2">
          Address 2
          <span class="text-muted">(Optional)</span>
        </label>
        <input
          v-model="$v.address_2.$model"
          type="text"
          class="form-control"
          id="address2"
          placeholder="Apartment or suite"
        />
      </div>

      <div class="row">
        <div class="col-md-5 mb-3">
          <label for="country">
            Country
            <span class="text-danger">*</span>
          </label>
          <select
            v-model="$v.country.$model"
            :class="{'is-invalid': validationStatus($v.country)}"
            class="custom-select d-block w-100"
            id="country"
            required
          >
            <option value>Choose...</option>
            <option>United States</option>
          </select>
          <div v-if="!$v.country.required" class="invalid-feedback">Please select a valid country.</div>
        </div>
        <div class="col-md-4 mb-3">
          <label for="state">
            State
            <span class="text-danger">*</span>
          </label>
          <select
            v-model="$v.state.$model"
            :class="{'is-invalid': validationStatus($v.state)}"
            class="custom-select d-block w-100"
            id="state"
            required
          >
            <option value>Choose...</option>
            <option>California</option>
          </select>
          <div v-if="!$v.state.required" class="invalid-feedback">Please provide a valid state.</div>
        </div>
        <div class="col-md-3 mb-3">
          <label for="zip">
            Zip
            <span class="text-danger">*</span>
          </label>
          <input
            v-model="$v.zip.$model"
            type="text"
            :class="{'is-invalid': validationStatus($v.zip)}"
            class="form-control"
            id="zip"
            placeholder
            required
          />
          <div v-if="!$v.zip.required" class="invalid-feedback">Zip code required.</div>
        </div>
      </div>
      <!-- <hr class="mb-4" />
      <div class="custom-control custom-checkbox">
        <input type="checkbox" class="custom-control-input" id="same-address" />
        <label
          class="custom-control-label"
          for="same-address"
        >Shipping address is the same as my billing address</label>
      </div>
      <div class="custom-control custom-checkbox">
        <input type="checkbox" class="custom-control-input" id="save-info" />
        <label class="custom-control-label" for="save-info">Save this information for next time</label>
      </div>
      <hr class="mb-4" />

      <h4 class="mb-3">Payment</h4>-->

      <!-- <div class="d-block my-3">
        <div class="custom-control custom-radio">
          <input
            id="credit"
            name="paymentMethod"
            type="radio"
            class="custom-control-input"
            checked
            required
          />
          <label class="custom-control-label" for="credit">Credit card</label>
        </div>
        <div class="custom-control custom-radio">
          <input id="debit" name="paymentMethod" type="radio" class="custom-control-input" required />
          <label class="custom-control-label" for="debit">Debit card</label>
        </div>
        <div class="custom-control custom-radio">
          <input
            id="paypal"
            name="paymentMethod"
            type="radio"
            class="custom-control-input"
            required
          />
          <label class="custom-control-label" for="paypal">PayPal</label>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6 mb-3">
          <label for="cc-name">Name on card</label>
          <input type="text" class="form-control" id="cc-name" placeholder required />
          <small class="text-muted">Full name as displayed on card</small>
          <div class="invalid-feedback">Name on card is required</div>
        </div>
        <div class="col-md-6 mb-3">
          <label for="cc-number">Credit card number</label>
          <input type="text" class="form-control" id="cc-number" placeholder required />
          <div class="invalid-feedback">Credit card number is required</div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-3 mb-3">
          <label for="cc-expiration">Expiration</label>
          <input type="text" class="form-control" id="cc-expiration" placeholder required />
          <div class="invalid-feedback">Expiration date required</div>
        </div>
        <div class="col-md-3 mb-3">
          <label for="cc-cvv">CVV</label>
          <input type="text" class="form-control" id="cc-cvv" placeholder required />
          <div class="invalid-feedback">Security code required</div>
        </div>
      </div>
      <hr class="mb-4" />-->
      <button
        @click="submit()"
        type="button"
        class="btn btn-primary btn-lg btn-block mb-5"
      >Continue to checkout</button>
    </form>
  </div>
</template>

<script>
import { required, email } from "vuelidate/lib/validators";

export default {
  name: "CheckoutForm",

  data() {
    return {
      first_name: "",
      last_name: "",
      email: "",
      phone: "",
      address_1: "",
      address_2: "",
      country: "",
      state: "",
      zip: "",
    };
  },

  validations: {
    first_name: { required },
    last_name: { required },
    email: { required, email },
    phone: { required },
    address_1: { required },
    address_2: {},
    country: { required },
    state: { required },
    zip: { required },
  },

  methods: {
    validationStatus(validation) {
      return typeof validation != "undefined" ? validation.$error : false;
    },

    submit() {
      this.$v.$touch();
      if (this.$v.$pendding || this.$v.$error) return;

      alert("Data Submit");
    },
  },
};
</script>

