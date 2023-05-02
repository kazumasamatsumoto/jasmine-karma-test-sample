import { HttpClientModule } from '@angular/common/http';
import { NgModule } from '@angular/core';
import { FormGroup, FormsModule, ReactiveFormsModule } from '@angular/forms';
import { BrowserModule } from '@angular/platform-browser';
import { RouterModule, Routes } from '@angular/router';
import { NgMultiSelectDropDownModule } from 'ng-multiselect-dropdown';
//import { routes } from '../app-routing.module';
import { EmployeeComponent } from './employee.component';

const routes: Routes = [
    {

        path: '', component: EmployeeComponent

    }
]

@NgModule({
    declarations: [

        EmployeeComponent

    ],
    imports: [
        RouterModule.forChild(routes)

    ],
    providers: [],

})
export class LazyModule { }
