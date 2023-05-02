import { Component } from '@angular/core';
import { FormBuilder, FormGroup } from '@angular/forms';
import { IDropdownSettings } from 'ng-multiselect-dropdown';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  dropdownData : any[] = [];  
  settings:IDropdownSettings={};
  form!:FormGroup;
  selectedItems: any[] = [] ;
  
  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    this.dropdownData = [
      { ID: 1, Value: 'Data1' },
      { ID: 2, Value: 'Data2' },
      { ID: 3, Value: 'Data3' },
      { ID: 4, Value: 'Data4' },
      { ID: 5, Value: 'Data5' }
    ];
    this.settings = {
      idField: 'ID',
      textField: 'Value',     
      selectAllText: "Select All Data",
      unSelectAllText: "UnSelect All Data",
      allowSearchFilter: true,
      noDataAvailablePlaceholderText: "Nothing to show data"
    };
    this.selectedItems = [
      { ID: 3, Value: 'Data4'  },
      { ID: 4,Value: 'Data5' }
    ];
    this.form = this.fb.group({
      myItems: [this.selectedItems]
  });
  }

  onDataSelect(item: any) {
    console.log('onData Select', item);
  }
  onDataUnSelect(item: any) {
    console.log('onData UnSelect', item);
  }
  onSelectAll(items: any) {
    console.log('onSelect All', items);
  }
  onUnSelectAll() {
    console.log('onUnSelect All fires');
  }
}
