import { HttpClientModule } from '@angular/common/http';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { StudentService } from './services/student.service';
import { HttpClientTestingModule } from '@angular/common/http/testing';
import { StudentComponent } from '../app/student/student.component';
import { FormBuilder, FormsModule, ReactiveFormsModule } from '@angular/forms';
import { BrowserModule, By } from '@angular/platform-browser';
import { DotnetofficeComponent } from '../app/dotnetoffice/dotnetoffice.component';
import { AppRoutingModule, routes } from './app-routing.module';
import { Router, RouterLinkWithHref } from '@angular/router';
import { RouterTestingModule } from '@angular/router/testing';
import { AppComponent } from './app.component';

import { Location } from "@angular/common";

describe('AppRouting module', () => {
    let component: StudentComponent;
    let appcomp: AppComponent;
    let fixture: ComponentFixture<StudentComponent>;
    let appfixture: ComponentFixture<AppComponent>;

    let objRouter: Router;
    let location: Location;

    beforeEach(async () => {
        await TestBed.configureTestingModule({
            declarations: [StudentComponent, DotnetofficeComponent, AppComponent],
            providers: [StudentService],
            imports: [HttpClientModule, HttpClientTestingModule, FormsModule, ReactiveFormsModule, HttpClientModule, AppRoutingModule,
                RouterTestingModule.withRoutes(routes)]
        })
            .compileComponents();


        objRouter = TestBed.inject(Router);
        location = TestBed.inject(Location);

        fixture = TestBed.createComponent(StudentComponent);
        component = fixture.componentInstance;

        fixture.detectChanges();
        appfixture = TestBed.createComponent(AppComponent);
        appcomp = appfixture.componentInstance;
        objRouter.initialNavigation();


    });

    beforeEach(() => {

    })


    // it('Unit test case for default route', async () => {

    //     appfixture.detectChanges();

    //     appfixture.whenStable().then(() => {
    //         expect(location.path()).toEqual("/student");

    //     })
    // });


    it('Unit test case for student route', async() => {

        appfixture.detectChanges();

        let link = appfixture.debugElement.queryAll(By.directive(RouterLinkWithHref));
        link[0].nativeElement.click();
        appfixture.whenStable().then(() => {
            expect(location.path()).toEqual("/student");

        })
    });

});
