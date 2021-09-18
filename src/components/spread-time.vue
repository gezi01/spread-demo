
<template>
  <div class="sample-tutorial">
    <gc-spread-sheets class="sample-spreadsheets" @workbookInitialized="initSpread"></gc-spread-sheets>
  </div>
</template>

<script>
  import Vue from "vue";
  import '@grapecity/spread-sheets-resources-zh';
  GC.Spread.Common.CultureManager.culture("zh-cn");
  import "@grapecity/spread-sheets-vue";
  import GC from "@grapecity/spread-sheets";
  export default {
    name:'spread',
    data(){
      return {
        spread: null
      }
    },
    methods:{
      initSpread(spread){
        let sheet = spread.getSheet(0);
        // var sheet = spread.getActiveSheet();
        sheet.suspendPaint();
        let showTimeStyle = new GC.Spread.Sheets.Style();


        showTimeStyle.cellButtons = [{
          imageType: GC.Spread.Sheets.ButtonImageType.dropdown,
          command: "openDateTimePicker",
          useButtonStyle: true,
        }];
        showTimeStyle.dropDowns = [{
          type: GC.Spread.Sheets.DropDownType.dateTimePicker,
          option: {
            showTime: false
          }
        }];
        // sheet.setText(0, 1, "Date Time Picker (showTime: true)");
        sheet.setStyle(2,1, showTimeStyle,);
        sheet.setStyle(3,1, showTimeStyle,);
        sheet.setStyle(4,1, showTimeStyle,);
        sheet.setText(0, 1, "DatePicker", GC.Spread.Sheets.SheetArea.colHeader);
        var range = sheet.getRange(-1, 1, -1 ,1);
        range.width(150);
        range.formatter("yyyy年MM月dd日");
        sheet.resumePaint();

        // spread.commandManager().execute({
        //   cmd: "openDateTimePicker",
        //   row: 2,
        //   col: 5,
        //   sheetName: "Sheet1"
        // });
      },
    }
  }
</script>

<style scoped>
  .sample-tutorial {
    position: relative;
    height: 600px;
    overflow: hidden;
  }

  .sample-spreadsheets {
    width: 100%;
    height: 100%;
    overflow: hidden;
    float: left;
  }

  body {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
  }
</style>


