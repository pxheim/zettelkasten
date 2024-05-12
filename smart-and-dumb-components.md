Common design principle where you have a single smart component that handles all the business logic and then passes down data to be displayed to child (dumb) components that only worry about layout. Typically a "screen" component would be the smart component and all child components would be the dumb ones.

# Testing examples

Angular testing **input** of **dumb** component:

```ts
describe('input: apiaries', () => {    
  it('should show a list of starred apiaries', () => {  
    // ARRANGE  
    const starredApiaries = [{ id: '1', name: '1', starred: true }];  
    component.apiaries = starredApiaries;  
  
    // ACT  
    fixture.detectChanges();  
  
    // ASSERT  
    expect(  
      fixture.debugElement.queryAll(  
        By.css('[data-testid="starred-apiary-list-item"]'),  
      ).length,  
    ).toEqual(starredApiaries.length);  
  });  
});
```

Angular testing **output** of **dumb** component:

```ts
describe('output: addApiary', () => {  
  it('should emit when user clicks on add apiary', () => {  
    // ARRANGE  
    const observerSpy = subscribeSpyTo(component.addApiary);  
    const addButton = fixture.debugElement.query(  
      By.css('[data-testid="add-apiary-button"]'),  
    );  
  
    // ACT  
    addButton.nativeElement.click();  
  
    // ASSERT  
    expect(observerSpy.getValuesLength()).toEqual(1);  
  });  
});
```

Angular testing **input** of **smart** component:

```ts
describe('input: apiaries', () => {  
  it('should use the apiaries selector as input', () => {  
    // ARRANGE  
    let sidebar = fixture.debugElement.query(By.css('px-sidebar'));  
  
    // ASSERT  
    expect(sidebar.componentInstance.apiariesSignal()).toEqual(  
      mockApiaries,  
    );  
  });  
});
```

Angular testing **output** of **smart** component:

```ts
describe('output: addApiary', () => {  
  it('should open a modal', () => {  
    // ARRANGE  
    const modal = fixture.debugElement.query(By.css('px-modal'));  
    let sidebar = fixture.debugElement.query(By.css('px-sidebar'));  
  
    // ACT  
    sidebar.triggerEventHandler('addApiary');  
    fixture.detectChanges();  
  
    // ASSERT  
    expect(modal.componentInstance.isOpen).toBeTruthy();  
  });  
});
```
