<script setup>
import CartBoxone from '@/components/cartBoxone.vue'
import AeraButton from '@/components/AeraButton.vue'
import BottomButton from '@/components/BottomButton.vue'
import ColumnButton from '@/components/ColumnButton.vue'
import SeclectBox from '@/components/SeclectBox.vue'
import cartBoxTowContent from '@/components/cartBoxTowContent.vue'
import cartBoxOneCentent from '@/components/cartBoxOneCentent.vue'
import {
  Demonstrationarea,
  AdvanceStartZone,
  WaterTownshipUnit,
  Ecologicalprotection,
  FarmlandHoldings,
  BlueGgreenspace,
  Widthgreen,
  Coverage,
  WaterSurfacerate
} from '@/server/db'
import P18 from '@/assets/images/P18.svg'
import P19 from '@/assets/images/P19.svg'
import P28 from '@/assets/images/P28.svg'
import P25 from '@/assets/images/P25.svg'
import P27 from '@/assets/images/P27.svg'
const siteIcon = ref([P18, P19])
const CoverageIcon = [P28, P25, P27]
const colors = [
  'linear-gradient(90deg, #503e2a 0%, #cdba55 100%)',
  'linear-gradient(90deg, #3d4a30 0%, #3fc894 100%)',
  'linear-gradient(90deg, #1c3d2c 0%, #4ca5cd 100%)'
]
</script>
<template>
  <div class="main">
    <AeraButton />

    <div class="banner">
      <BottomButton />
      <SeclectBox />
      <ColumnButton />
      <div class="left">
        <div class="one">
          <div class="titles">
            <div class="test1">
              {{ Demonstrationarea.title }}
            </div>
          </div>
          <div class="onebanner">
            <CartBoxone
              :width="'70.8rem'"
              :height="'25rem'"
              :title="Demonstrationarea.data.Targeting.title"
            >
              <textTitle :data="Demonstrationarea.data.Targeting"></textTitle>
            </CartBoxone>
            <CartBoxone
              :width="'49.7rem'"
              :height="'25rem'"
              :title="Demonstrationarea.data.Special.title"
            >
              <titleList :list="Demonstrationarea.data.Special.data"></titleList>
            </CartBoxone>
            <CartBoxtow :width="'39.999rem'" :height="'24.5rem'">
              <CircleChart
                :showPercentage="false"
                :centerValue="Demonstrationarea.data.ecologicalData.total"
                :showLegend="true"
                :legend="'right'"
                centerLabel="总计人口"
                :dataItems="Demonstrationarea.data.ecologicalData.data"
                :width="'39.999rem'"
                :height="'24.5rem'"
                :roseType="'pie'"
                :radius="['40%', '70%']"
                :isCircle="false"
                :center="['32%', '50%']"
                :titleLeft="'24.5%'"
                :LabelRight="'5%'"
              />
            </CartBoxtow>
            <CartBoxtow :width="'39.999rem'" :height="'24.5rem'">
              <ProgressAll
                :width="'34.78016rem'"
                :height="'20rem'"
                :colors="colors"
                :data="Demonstrationarea.data.ProportionUse"
              >
              </ProgressAll>
            </CartBoxtow>
            <CartBoxtow :width="'39.999rem'" :height="'24.5rem'">
              <ecologyTitle
                :width="'39.999rem'"
                :height="'24.5rem'"
                :data="Demonstrationarea.data.structure"
              >
              </ecologyTitle>
            </CartBoxtow>
          </div>
        </div>
        <div class="two">
          <div class="titles">
            <div class="test1">
              {{ AdvanceStartZone.title }}
            </div>
          </div>
          <div class="towbanner">
            <CartBoxone
              :width="'39.799rem'"
              :height="'24.20064rem'"
              :title="AdvanceStartZone.population.title"
            >
              <CircleChart
                :centerValue="AdvanceStartZone.population.ecologicalData.total"
                :showLegend="false"
                :centerLabel="AdvanceStartZone.population.ecologicalData.title"
                :dataItems="AdvanceStartZone.population.ecologicalData.data"
                :width="'39rem'"
                :height="'20rem'"
                :isCong="true"
                :radius="['45%', '55%']"
                :radiusCong="['42%', '58%']"
              />
            </CartBoxone>
            <CartBoxone
              :width="'39.799rem'"
              :height="'24.20064rem'"
              :title="AdvanceStartZone.structure.title"
            >
              <cartBoxOneCentent></cartBoxOneCentent>
            </CartBoxone>
            <CartBoxone
              :width="'39.799rem'"
              :height="'24.20064rem'"
              :title="AdvanceStartZone.site.title"
            >
              <ProgressAll
                :data="AdvanceStartZone.site.data"
                :icon="siteIcon"
                :width="'39.799rem'"
              ></ProgressAll>
            </CartBoxone>
          </div>
        </div>
        <div class="three">
          <div class="titles">
            <div class="test1">
              {{ WaterTownshipUnit.title }}
            </div>
          </div>
          <div class="threebanner">
            <CartBoxtow v-for="i in WaterTownshipUnit.data" :width="'40rem'" :height="'14.8rem'">
              <cartBoxTowContent
                :image="i.image"
                :text="i.text"
                :count="i.count"
              ></cartBoxTowContent>
            </CartBoxtow>
          </div>
        </div>
      </div>
      <div class="right">
        <div class="blist">
          <StructureButton />
        </div>
        <div class="carts">
          <CartBoxone :width="'60.5rem'" :height="'34.1rem'" :title="Ecologicalprotection.title">
            <CircleChart
              :centerValue="Ecologicalprotection.total"
              :showLabel="true"
              :centerLabel="Ecologicalprotection.centerTitle"
              :dataItems="Ecologicalprotection.data"
              :width="'55.3472rem'"
              :height="'32.3712rem'"
              :isCong="true"
              :center="['50%', '43%']"
              :titleTop="'32%'"
            />
          </CartBoxone>
          <CartBoxone :width="'60.5rem'" :height="'34.1rem'" :title="FarmlandHoldings.title">
            <CircleChart
              :centerValue="FarmlandHoldings.total"
              :centerLabel="FarmlandHoldings.centerTitle"
              legend="right"
              :dataItems="FarmlandHoldings.data"
              :width="'55.3472rem'"
              :height="'32.3712rem'"
              :isCong="true"
              :center="['36%', '49%']"
              :titleLeft="'32%'"
            />
          </CartBoxone>
          <CartBoxone :width="'60.5rem'" :height="'34.1rem'" :title="BlueGgreenspace.title">
            <BarCharts
              :x-axis-data="BlueGgreenspace.data.xAxisdata"
              :series-data="BlueGgreenspace.data.seriesdata"
              theme="dark"
              :horizontal="false"
            />
          </CartBoxone>
          <CartBoxone :width="'60.5rem'" :height="'34.1rem'" :title="WaterSurfacerate.title">
            <gauges></gauges>
          </CartBoxone>
          <CartBoxone :width="'60.5rem'" :height="'34.1rem'" :title="Widthgreen.title">
            <BarCharts
              :x-axis-data="Widthgreen.data.xAxisdata"
              :series-data="Widthgreen.data.seriesdata"
              theme="dark"
              :horizontal="false"
            />
          </CartBoxone>
          <CartBoxtow :width="'60.5rem'" :height="'34.1rem'">
            <ProgressAll
              :isMax="true"
              :progwidth="' 39.88rem'"
              :icon="CoverageIcon"
              :data="Coverage.data"
            >
            </ProgressAll>
          </CartBoxtow>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.location-conditions {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.circle {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

/* .header {
  width: 100vw;
  height: 10.0694vh;
  border-radius: 0 0 0 0;
  opacity: 1;
  background: var(--header-brackground);
  margin-bottom: 1.7361vh;
} */

.main {
  width: 100%;
  height: 100%;
  padding: var(--content-padding);
}

.banner {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  font-family: 'SourceHanSansCN';

  .left {
    width: 145.2rem;
    height: 122.8rem;
    opacity: 1;
    align-items: start;

    .one {
      z-index: 1;
      width: 126rem;
      height: 63rem;
      border-radius: 1.15rem;
      opacity: 1;
      border: 0.1rem solid #2c3534;
      background: var(--backgrouend-tow);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-around;

      .titles {
        z-index: 2;
        width: 122rem;
        height: 5.2rem;
        border-radius: var(--border-radius);
        border: 0.1rem solid #314347;
        background: linear-gradient(90deg, #2a5934 0%, #1e3033 100%);
        margin-top: 1rem;

        .test1 {
          width: 30.8rem;
          height: 100%;
          z-index: 100;
          color: #fff;
          font-size: 2.8rem;
          display: flex;
          align-items: center;
          margin-left: 3rem;
          font-weight: 700;
        }
      }

      .onebanner {
        width: 122rem;
        height: 85%;
        /* background-color: #fff; */
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        align-content: space-around;
      }
    }

    .two {
      width: 125.8rem;
      height: 34.89994rem;
      border-radius: var(--border-radius);
      opacity: 1;
      border: 1px solid #2c3535;
      background: var(--backgrouend-tow);
      margin-top: 0.5rem;
      display: flex;
      align-items: center;
      justify-content: space-around;
      flex-direction: column;

      .titles {
        z-index: 2;
        width: 122rem;
        height: 5.2rem;
        height: 17%;
        border-radius: 0.5rem;
        border: 0.1rem solid #314347;
        background: linear-gradient(90deg, #2a5934 0%, #1e3033 100%);
        margin-top: 1.5rem;

        .test1 {
          width: 37rem;
          height: 100%;
          z-index: 100;
          color: #fff;
          font-size: 2.8rem;
          display: flex;
          align-items: center;
          margin-left: 3rem;
          font-weight: 700;
        }
      }

      .towbanner {
        width: 122rem;
        height: 85%;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        align-content: space-around;
      }
    }

    .three {
      width: 125.8rem;
      height: 25.49995rem;
      border-radius: 1.15rem;
      opacity: 1;
      border: 0.1rem solid #2c3534;
      background: var(--backgrouend-tow);
      margin-top: 1rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-around;

      .titles {
        z-index: 2;
        width: 122rem;
        height: 5.2rem;
        border-radius: 0.5rem;
        border: 1px solid #314347;
        background: linear-gradient(90deg, #2a5934 0%, #1e3033 100%);
        margin-top: 1.1rem;

        .test1 {
          width: 24.199rem;
          height: 100%;
          z-index: 100;
          color: #fff;
          font-size: 2.8rem;
          display: flex;
          align-items: center;
          margin-left: 3rem;
          font-weight: 700;
        }
      }

      .threebanner {
        width: 122rem;
        height: 70%;
        display: flex;
        justify-content: space-around;
        align-content: center;
      }
    }
  }

  .right {
    width: 125.6rem;
    align-items: end;
    height: 123.000048rem;
    border-radius: 1.6rem;
    opacity: 1;
    border: 0.1rem solid #456655;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    padding: 1rem;
    background: var(--backgrouend-tow);

    .blist {
      width: 98%;
      height: 12%;
    }

    .carts {
      width: 100%;
      height: 90%;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      align-items: center;
    }
  }
}
</style>
