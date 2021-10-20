<template>
  <div>
    <b-button v-b-modal.:id="modal.id">This is the SKAT Modal</b-button>

    <b-modal class="p-3" :id="modal.id" :static="true" hide-footer hide-header centered>
      <div class="text p-3">{{ modal.text }}</div>
        <b-row class="mx-3" v-if="input.enabled">
                  <div
                      :id="error.id"
                      class="text-danger"
                      v-if="input.enabled && this.inputValue === 'Wrong'"
                  >
                    {{ error.text }}
                  </div>
                <b-input
                    :id="input.id"
                    :required="input.required"
                    :placeholder="input.placeholder"
                    v-model="inputValue"
                ></b-input>
        </b-row>
      <b-row class="p-3 flex">
        <b-col>
                  <button
                      class="btn alt-btn float-left"
                      :class="cancel.class"
                      :id="cancel.id"
                      @click="cancelled()">
                    {{ cancel.text }}
                  </button>
        </b-col>
        <b-col>
            <button
                class="btn alt-btn float-right"
                :class="accept.class"
                :id="accept.id"
                @click="accepted()">
              {{ accept.text }}
            </button>
        </b-col>
      </b-row>
    </b-modal>
  </div>
</template>

<script lang="ts">

export default {
  name: "SkatModal",
  props: {
    modal: {
      type: Object,
      default: () => ({
        id: 'modal',
        text: ''
      })
    },
    cancel: {
      type: Object,
      default: () => ({
        class: '',
        id: 'modal-cancel',
        text: 'Annuller'
      })
    },
    accept: {
      type: Object,
      default: () => ({
        class: '',
        id: 'modal-accept',
        text: 'Gem'
      })
    },
    input: {
      type: Object,
      default: () => ({
        enabled: false,
        placeholder: '....',
        id: 'modal-input',
        required: false
      })
    },
    error: {
      type: Object,
      default: () => ({
        id: 'error',
        text: 'Input was invalid'
      })
    }
  },
  data () {
    return {
      inputValue: '',
      errorInput: 'Wrong'
    }
  },
  methods: {
    cancelled () {
      this.$bvModal.hide(this.modal.id)
      this.$emit('cancelled')
    },
    accepted () {
      this.$bvModal.hide(this.modal.id)
      this.$emit('accepted', this.inputValue)
    }
  }
}
</script>

