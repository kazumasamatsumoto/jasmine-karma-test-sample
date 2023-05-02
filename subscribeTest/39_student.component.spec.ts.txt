import { HttpClientModule } from '@angular/common/http';
import { ComponentFixture, fakeAsync, TestBed, tick } from '@angular/core/testing';
import { StudentService } from '../services/student.service';
import { HttpClientTestingModule } from '@angular/common/http/testing';
import { StudentComponent } from './student.component';
import { FormBuilder, FormsModule, ReactiveFormsModule } from '@angular/forms';
import { BrowserModule } from '@angular/platform-browser';
import { DotnetofficeComponent } from '../dotnetoffice/dotnetoffice.component';
import { AppRoutingModule } from '../app-routing.module';
import { AppComponent } from '../app.component';
import { of, subscribeOn } from 'rxjs';
import { PostModel } from '../PostModel';


describe('StudentComponent', () => {
  let component: StudentComponent;
  let fixture: ComponentFixture<StudentComponent>;
  let service: StudentService;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [StudentComponent, AppComponent],
      imports: [HttpClientModule, FormsModule, AppRoutingModule],
      providers: [StudentService]
    })
      .compileComponents();

    fixture = TestBed.createComponent(StudentComponent);
    component = fixture.componentInstance;

    service = TestBed.inject(StudentService);
    fixture.detectChanges();
  });

  it('unit test for subscribe method', fakeAsync(() => {

    let spy = spyOn(service, 'getListOfData').and.returnValue(of([]));
    let subSpy = spyOn(service.getListOfData(), 'subscribe');
    component.ngOnInit();
    tick();
    expect(spy).toHaveBeenCalledBefore(subSpy);
    expect(subSpy).toHaveBeenCalled();
  }));

  
  it('unit test for inside subscribe method', fakeAsync(() => {

    const testpost  : PostModel[] = [
      {id:1,userId:1,title:'title 1', body:'body1'},
      {id:2,userId:2,title:'title 2', body:'body2'},

    ];
    let spy = spyOn(service, 'getListOfData').and.returnValue(of(testpost));
   
    
    component.ngOnInit();
    tick();
    expect(component.postData).toBeDefined();
    expect(component.postData.length).toEqual(2);
  }));


});
