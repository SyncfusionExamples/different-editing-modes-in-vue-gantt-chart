<template>
  <ejs-gantt :dataSource="data"
             :taskFields="taskFields"
             :editSettings="editOptions"
             :toolbar="toolbarOptions"
             :treeColumnIndex="1"
             :allowSelection="true"
             :height="450">
    <e-columns>
      <e-column field="TaskID" headerText="Task ID" width="100" textAlign="Right"></e-column>
      <e-column field="TaskName" headerText="Task Name" textAlign="Left" width="200"></e-column>
      <e-column field="StartDate" headerText="Start Date" textAlign="Right" format="dd/MM/yyyy" width="120"></e-column>
      <e-column field="Duration" headerText="Duration" textAlign="Right" width="120"></e-column>
    </e-columns>
  </ejs-gantt>
</template>

<script>
import {GanttComponent, ColumnsDirective, ColumnDirective, Edit, Toolbar, Selection} from '@syncfusion/ej2-vue-gantt'
import {projectNewData} from './data.js'
export default {
  name: 'App',
  components: {
    'ejs-gantt': GanttComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  provide:{
    gantt: [Edit, Toolbar, Selection]
  },
  data(){
    return{
      data: projectNewData,
      editOptions:{
        allowEditing: true,
        allowAdding: true,
        allowDeleting: true,
        allowTaskbarEditing: true,
        mode: 'Auto'
      },
      toolbarOptions: ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll',
                      'Indent', 'Outdent'],
      taskFields:{
        id: 'TaskID',
        name: 'TaskName',
        startDate: 'StartDate',
        endDate: 'EndDate',
        duration: 'Duration',
        progress: 'Progress',
        dependency: 'Predecessor',
        child: 'subtasks'
      },
    }
  }
}
</script>

<style>
@import url("https://cdn.syncfusion.com/ej2/material.css");
</style>
