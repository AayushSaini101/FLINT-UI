<template>
  <div class="mt-14 flex items-center justify-center">
    <a-row class="p-4 w-full" :gutter="[24, 32]">
      <a-col :xs="{ span: 24 }" :md="{ span: 12 }" :xl="{ span: 6 }">
        <a-row class="cards flex justify-between" :gutter="[6, 6]">
          <a-col
            :xs="{ span: 24 }"
            :md="{ span: 20 }"
            :xl="{ span: 20 }"
            class="bg-gray-300 border border-gray-200 card-content rounded-lg"
          >
            <i class="fas fa-plus fa-lg" />
            <div class="bg-gray-200 rounded-r-lg body-step">
              <h2 class="font-bold text-sm">Create a new simulation</h2>
              <p class="text-xs text-gray-600">Click the new button below</p>
            </div>
          </a-col>
          <a-col class="next-icons" :xs="{ span: 24 }" :md="{ span: 4 }" :xl="{ span: 4 }">
            <i class="fas fa-arrow-right fa-2x" />
          </a-col>
        </a-row>
      </a-col>

      <a-col :xs="{ span: 24 }" :md="{ span: 12 }" :xl="{ span: 6 }">
        <a-row class="cards flex justify-between" :gutter="[6, 6]">
          <a-col
            :xs="{ span: 24 }"
            :md="{ span: 20 }"
            :xl="{ span: 20 }"
            class="bg-gray-300 border border-gray-200 card-content rounded-lg"
          >
            <i class="fas fa-file fa-lg" />
            <div class="bg-gray-200 rounded-r-lg body-step">
              <h2 class="font-bold text-sm">Upload file</h2>
              <p class="text-xs text-gray-600">Dataset file for GCBM</p>
            </div>
          </a-col>
          <a-col class="next-icons" :xs="{ span: 24 }" :md="{ span: 4 }" :xl="{ span: 4 }">
            <i class="fas fa-arrow-right fa-2x" />
          </a-col>
        </a-row>
      </a-col>

      <a-col :xs="{ span: 24 }" :md="{ span: 12 }" :xl="{ span: 6 }">
        <a-row class="cards flex justify-between" :gutter="[6, 6]">
          <a-col
            :xs="{ span: 24 }"
            :md="{ span: 20 }"
            :xl="{ span: 20 }"
            class="bg-gray-300 border border-gray-200 card-content rounded-lg"
          >
            <i class="fas fa-cogs fa-lg" />
            <div class="bg-gray-200 rounded-r-lg body-step">
              <h2 class="font-bold text-sm">Configure</h2>
              <p class="text-xs text-gray-600">Change configuration parameters</p>
            </div>
          </a-col>
          <a-col class="next-icons" :xs="{ span: 24 }" :md="{ span: 4 }" :xl="{ span: 4 }">
            <i class="fas fa-arrow-right fa-2x" />
          </a-col>
        </a-row>
      </a-col>

      <a-col :xs="{ span: 24 }" :md="{ span: 12 }" :xl="{ span: 6 }">
        <a-row class="cards flex justify-between" :gutter="[6, 6]">
          <a-col
            :xs="{ span: 24 }"
            :md="{ span: 20 }"
            :xl="{ span: 20 }"
            class="bg-gray-300 border border-gray-200 card-content rounded-lg"
          >
            <i class="fas fa-check fa-lg" />
            <div class="bg-gray-200 rounded-r-lg body-step">
              <h2 class="font-bold text-sm">Run</h2>
              <p class="text-xs text-gray-600">Run the simulation with new configs</p>
            </div>
          </a-col>
          <a-col class="next-icons" :xs="{ span: 24 }" :md="{ span: 4 }" :xl="{ span: 4 }"> </a-col>
        </a-row>
      </a-col>
    </a-row>
  </div>
</template>

<style scoped>
.cards {
  display: flex;
  align-items: center;
}
.card-content {
  display: flex;
  align-items: center;
  max-width: 250px;
}
.card-content > i {
  margin: 10px;
}
.card-content > div {
  margin: 10px;
  padding: 5px 10px;
  height: 100px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.next-icons {
  margin-left: 10px;
}
@media screen and (max-width: 768px) {
  .cards {
    flex-direction: column;
  }
  .next-icons {
    display: flex;
    justify-content: center;
    transform: rotate(90deg);
    margin-left: 0px;
    margin-top: 20px;
  }
}
@media screen and (max-width: 768px) {
  .card-content {
    max-width: 300px;
  }
  .card-content > div {
    margin: 20px;
    padding: 10px 20px;
  }
  .card-content > i {
    margin: 20px;
  }
}
@media screen and (max-width: 350px) {
  .card-content > div {
    margin: 10px;
    padding: 10px;
  }
  .card-content > i {
    margin: 10px;
  }
}
</style>
