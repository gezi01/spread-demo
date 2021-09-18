
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
      initSpread(spread) {
        let sheet = spread.getSheet(0);
        sheet.suspendPaint();

        // -------------------- Date Time Picker : showTime true ---------------------
        let showTimeStyle = new GC.Spread.Sheets.Style();
        showTimeStyle.cellButtons = [{
          imageType: GC.Spread.Sheets.ButtonImageType.dropdown,
          command: "openDateTimePicker",
          useButtonStyle: true,
        }];
        showTimeStyle.dropDowns = [{
          type: GC.Spread.Sheets.DropDownType.dateTimePicker,
          option: {
            showTime: true
          }
        }];
        sheet.setText(1, 2, "Date Time Picker (showTime: true)");
        sheet.setStyle(2, 5, showTimeStyle);

        // -------------------- Date Time Picker : showTime False ---------------------
        let notShowTimestyle = new GC.Spread.Sheets.Style();
        notShowTimestyle.cellButtons = [{
          imageType: GC.Spread.Sheets.ButtonImageType.dropdown,
          command: "openDateTimePicker",
          useButtonStyle: true,
        }];
        notShowTimestyle.dropDowns = [{
          type: GC.Spread.Sheets.DropDownType.dateTimePicker,
          option: {
            showTime: false
          }
        }];
        sheet.setText(20, 2, "Date Time Picker (showTime: false)");
        sheet.setStyle(21, 5, notShowTimestyle);

        // -------------------- Date Time Picker : CalendarPage - Year ---------------------
        let calendarYearStyle = new GC.Spread.Sheets.Style();
        calendarYearStyle.cellButtons = [{
          imageType: GC.Spread.Sheets.ButtonImageType.dropdown,
          command: "openDateTimePicker",
          useButtonStyle: true,
        }];
        calendarYearStyle.dropDowns = [{
          type: GC.Spread.Sheets.DropDownType.dateTimePicker,
          option: {
            showTime: true,
            calendarPage: GC.Spread.Sheets.CalendarPage.year,
          }
        }];
        sheet.setText(20, 8, "Date Time picker (calendarPage - Year)");
        sheet.setStyle(21, 11, calendarYearStyle);

        // -------------------- Date Time Picker : CalendarPage - Month ---------------------
        let calendarMonthStyle = new GC.Spread.Sheets.Style();
        calendarMonthStyle.cellButtons = [{
          imageType: GC.Spread.Sheets.ButtonImageType.dropdown,
          command: "openDateTimePicker",
          useButtonStyle: true,
        }];
        calendarMonthStyle.dropDowns = [{
          type: GC.Spread.Sheets.DropDownType.dateTimePicker,
          option: {
            showTime: true,
            calendarPage: GC.Spread.Sheets.CalendarPage.month,
          }
        }];
        sheet.setText(1, 8, "Date Time picker (calendarPage - Month)");
        sheet.setStyle(2, 11, calendarMonthStyle);

        sheet.resumePaint();

        spread.commandManager().execute({
          cmd: "openDateTimePicker",
          row: 2,
          col: 5,
          sheetName: "Sheet1"
        });
      }
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


