<template>
    <Page>
<StackLayout>
    <GridLayout rows="auto, auto, *"
                columns="auto, *">
        <DropDown ref="dd"
                  backroundColor="red"
                  :items="items"
                  :selectedIndex="selectedIndex"
                  @selectedIndexChanged="onchange"
                  @opened="onopen"
                  @closed="onclose"
                  row="0"
                  colSpan="2"></DropDown>
        <Label text="Selected Index:"
               row="1"
               col="0"
               fontSize="18"
               verticalAlignment="bottom"></Label>
        <Label :text="selectedIndex"
                   row="1"
                   col="1"></Label>
    </GridLayout>
</StackLayout>
    </Page>
</template>

<script>
import { SelectedIndexChangedEventData } from "nativescript-drop-down";

export default {
  data() {
    return {
      selectedIndex: 1,
      items: []
    };
  },
  mounted() {
    this.items = [];
    for (var i = 0; i < 5; i++) {
      this.items.push("data item " + i);
    }
  },
  methods: {
    onchange(args) {
      this.selectedIndex = args.newIndex;
      console.log(
        `Drop Down selected index changed from ${args.oldIndex} to ${
          args.newIndex
        }`
      );
    },

    onopen() {
      console.log("Drop Down opened.");
    },

    onclose() {
      console.log("Drop Down closed.");
    }
  }
};
</script>

<style scoped>
Dropdown {
  padding: 20;
}
</style>
