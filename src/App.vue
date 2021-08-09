<template>
    <ejs-maps :titleSettings='titleSettings' :legendSettings='legendSettings'>
        <e-layers>
            <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' :dataLabelSettings='dataLabelSettings' :tooltipSettings='tooltipSettings'></e-layer>
        </e-layers>
    </ejs-maps>
</template>

<script>
import { MapsComponent, LayersDirective, LayerDirective, MapAjax, Legend, DataLabel, MapsTooltip } from '@syncfusion/ej2-vue-maps'

export default {
  name: 'App',
  components: {
    'ejs-maps': MapsComponent,
    'e-layers': LayersDirective,
    'e-layer': LayerDirective 
  },
  data() {
    return {
      titleSettings: {
          text: 'UN security council countries'
      },
      shapeData: new MapAjax('https://cdn.syncfusion.com/maps/map-data/world-map.json'),
      dataSource: [{  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}],
      shapePropertyPath: 'name',
      shapeDataPath: 'Country',
      shapeSettings: {
            colorValuePath: 'Membership',
            colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }
            ]
      },
      dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            smartLabelMode: 'Trim'
      },
      legendSettings: {
          visible: true
      },
      tooltipSettings: {
          visible: true,
          valuePath: 'Country'
      }
    }
  },
  provide: {
    maps: [ Legend, DataLabel, MapsTooltip ]
  }
}
</script>
