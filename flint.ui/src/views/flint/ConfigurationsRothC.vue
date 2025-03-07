<template>
  <div>
    <div class="mb-10 mx-5 md:justify-center">
      <LandingPageNavbar />
      <div class="px-8 pb-6 sm:px-16 md:px-24">
        <div>
          <h2 class="mb mt-7 py-4 text-2xl text-earth">RothC example simulation configuration</h2>
          <p class="text-earth sm:text-base">
            Was the simulation conducted at a specific place ? Click
            <span>here</span> to save latitude and longitude co-ordinates
          </p>
          <p class="text-earth text-base">
            Input the custom values in the fields below. Default values as placeholder text will be used if none
            provided.
          </p>
        </div>

        <div class="mt-10">
          <div>
            <div class="py-6 mb-3">
              <h2 class="text-xl font-normal text-earth">Start and End date of simulation</h2>
              <div>
                <div class="text-2xl font-normal text-gray"><Datepicker size="small" /></div>
              </div>
            </div>
          </div>
        </div>

        <h2 class="mt-7 py-4 text-2xl font-normal text-earth">Configure Parameters</h2>

        <a-collapse accordion :bordered="false" class="rothcAccordion" @change="changeActiveKey">
          <a-collapse-panel
            v-for="(item, index) in configurations"
            :key="index"
            :header="`${item.text} (${item.type})`"
            :show-arrow="false"
          >
            <a-icon slot="extra" type="right" :rotate="accordionActiveKey == index ? 90 : 0" />
            <div :is="item.component" />
          </a-collapse-panel>
        </a-collapse>

        <div class="my-16 flex gap-8 items-center">
          <div data-v-step="5"><Button @click.native="apiRoute_rothc">Run</Button></div>
          <div v-show="clickedRun" data-v-step="6">
            <Button :btn-size="'auto'" @click.native="showTable ? hideRothCOuterTable() : showRothCOuterTable()">
              {{ showTable ? 'Hide' : 'Show' }} Output
            </Button>
          </div>
        </div>
        <RothCOuterTable v-if="showTable" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import RothCTemplate from '@/views/flint/RothCTemplate.vue'
import Datepicker from '@/components/Datepicker/DatepickerRothC.vue'
import LandingPageNavbar from '../../components/Navbars/LandingPageNavbar.vue'
import Button from '@/components/Button/Button.vue'
import Footer from '@/components/Footer/Footer.vue'
import RothCOuterTable from './RothCOuterTable.vue'
import RothCAvgAirTempVue from '@/components/ConfigurationsRothC/RothCAvgAirTemp.vue'
import RothCSoilCoverVue from '@/components/ConfigurationsRothC/RothCSoilCover.vue'
import RothCSoilVue from '@/components/ConfigurationsRothC/RothCSoil.vue'
import RothCInitSoilVue from '@/components/ConfigurationsRothC/RothCInitSoil.vue'
import RothCPresCMVue from '@/components/ConfigurationsRothC/RothCPresCM.vue'
import RothCOpenPanEvapVue from '@/components/ConfigurationsRothC/RothCOpenPanEvap.vue'
import RothCRainfallVue from '@/components/ConfigurationsRothC/RothCRainfall.vue'

export default {
  components: {
    RothCTemplate,
    Datepicker,
    LandingPageNavbar,
    RothCOuterTable,
    Button,
    Footer
  },
  data: function () {
    return {
      showTable: false,
      clickedRun: false,
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
      accordionActiveKey: '1',
      configurations: {
        rainfall: {
          component: RothCRainfallVue,
          type: 'rainfall',
          text: 'Rainfall'
        },
        openPanEvap: {
          component: RothCOpenPanEvapVue,
          type: 'openPanEvap',
          text: 'Open Pan Evaporation'
        },
        avgAirTemp: {
          component: RothCAvgAirTempVue,
          type: 'avgAirTemp',
          text: 'Average Air Temperature'
        },
        presCM: {
          component: RothCPresCMVue,
          type: 'presCM',
          text: 'Organic carbon inputs'
        },
        soilCover: {
          component: RothCSoilCoverVue,
          type: 'soilCover',
          text: 'Soil Cover'
        },
        initSoil: {
          component: RothCInitSoilVue,
          type: 'initSoil',
          text: 'Initial conditions of the Soil'
        },
        soil: {
          component: RothCSoilVue,
          type: 'soil',
          text: 'Soil characteristics'
        }
      }
    }
  },
  methods: {
    apiRoute_rothc() {
      // sending the new rothc config
      console.log('ROTHC route invoked with new configs')
      this.$store.dispatch('send_rothcConfig', { root: true })
      this.clickedRun = true
    },

    showRothCOuterTable() {
      this.$store.dispatch('parse_RothC_results')
      this.showTable = true
    },

    hideRothCOuterTable() {
      this.showTable = false
    },

    changeActiveKey(key) {
      this.accordionActiveKey = key
    }
  }
}
</script>
<style>
.rothcAccordion .anticon svg {
  transition: transform 0.3s ease;
}
.rothcAccordion .ant-collapse-header {
  font-size: 18px;
  color: theme('colors.earth') !important;
}
</style>
