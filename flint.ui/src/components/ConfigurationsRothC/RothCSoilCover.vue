<template>
  <div class="flex flex-wrap">
    <div class="w-full content-center rounded-md">
      <h1 class="flex-auto text-base text-earth font-normal">soilCover - data_orig</h1>
      <textarea
        v-model="newconfig_soilcover_data_orig"
        class="form-textarea rounded-md mt-1 block w-full"
        rows="5"
        placeholder=""
      >
      </textarea>
    </div>

    <div class="w-full content-center rounded-md mt-5">
      <h1 class="flex-auto text-base text-earth font-normal">soilCover - data_firstmonthcopy</h1>
      <textarea
        v-model="newconfig_soilcover_data_firstmonthcopy"
        class="form-textarea rounded-md mt-1 block w-full"
        rows="5"
        placeholder=""
      >
      </textarea>
    </div>

    <div class="w-full content-center rounded-md mt-5">
      <h1 class="flex-auto text-base text-earth font-normal">soilCover - data_month_avg</h1>
      <textarea
        v-model="newconfig_soilcover_data_month_avg"
        class="form-textarea rounded-md mt-1 block w-full"
        rows="5"
        placeholder=""
      >
      </textarea>
    </div>

    <div class="w-full content-center rounded-md mt-5">
      <h1 class="flex-auto text-base text-earth font-normal">soilCover - data_lastyearcopy</h1>
      <textarea
        v-model="newconfig_soilcover_data_lastyearcopy"
        class="form-textarea rounded-md mt-1 block w-full"
        rows="5"
        placeholder=""
      >
      </textarea>
    </div>
  </div>
</template>

<script>
import formatData from '@/mixins/formatData'

export default {
  mixins: [formatData],
  computed: {
    newconfig_soilcover_data_orig: {
      get() {
        return this.formatArray(this.$store.state.rothc.config.Variables[12].soilCover.transform.data_orig)
      },
      set(newValue) {
        this.$store.commit('setNewConfig_soilCover_data_orig', '$#[ ' + newValue + ' ]$#')
      }
    },

    newconfig_soilcover_data_firstmonthcopy: {
      get() {
        return this.formatArray(this.$store.state.rothc.config.Variables[12].soilCover.transform.data_firstmonthcopy)
      },
      set(newValue) {
        this.$store.commit('setNewConfig_soilCover_data_firstmonthcopy', '$#[ ' + newValue + ' ]$#')
      }
    },

    newconfig_soilcover_data_month_avg: {
      get() {
        return this.formatArray(this.$store.state.rothc.config.Variables[12].soilCover.transform.data_month_avg)
      },
      set(newValue) {
        this.$store.commit('setNewConfig_soilCover_data_month_avg', '$#[ ' + newValue + ' ]$#')
      }
    },

    newconfig_soilcover_data_lastyearcopy: {
      get() {
        return this.formatArray(this.$store.state.rothc.config.Variables[12].soilCover.transform.data_lastyearcopy)
      },
      set(newValue) {
        this.$store.commit('setNewConfig_soilCover_data_lastyearcopy', '$#[ ' + newValue + ' ]$#')
      }
    }
  }
}
</script>
