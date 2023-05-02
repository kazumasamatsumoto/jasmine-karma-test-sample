import { HttpClientModule } from '@angular/common/http';
import { DebugElement } from '@angular/core';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { By } from '@angular/platform-browser';
import { of } from 'rxjs';
import { AppRoutingModule } from '../app-routing.module';
import { Addition } from '../Calculator';
import { StudentService } from '../services/student.service';

import { DotnetofficeComponent } from './dotnetoffice.component';

describe('DotnetofficeComponent', () => {
  let component: DotnetofficeComponent;
  let fixture: ComponentFixture<DotnetofficeComponent>;
  let h1: HTMLElement;
  let deb: DebugElement;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [DotnetofficeComponent],
      providers: [StudentService],
      imports: [AppRoutingModule, HttpClientModule]
    })
      .compileComponents();

    fixture = TestBed.createComponent(DotnetofficeComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
    deb = fixture.debugElement;

    h1 = fixture.nativeElement.querySelector('h1');
  });

    

  it("table colspan attribute test case", () => {
 
    const elemtnt  = fixture.debugElement.nativeElement.querySelector('#colId');
    expect(elemtnt.getAttribute('colspan')).toEqual(component.ColumnSpan.toString());
    
  });

  it("button  attribute test case", () => {
 
    const elemtnt  = fixture.debugElement.nativeElement.querySelector('#buttonid');
    expect(elemtnt.getAttribute('aria-label')).toEqual(component.arialable.toString());

    
  });


});
