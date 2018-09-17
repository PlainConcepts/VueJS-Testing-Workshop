# Unit testing with vue

You can check [this article about testing](https://medium.com/@CKGrafico/how-to-test-your-javascript-components-b64179c5f386) before start with the workshop.
Remember that all the examples are only examples, not necessary the best practise.

1. Testing services/actions/helpers
- Test all the public methods

2. Testing components
- Test only logic, not UI (use e2e for that)
- Try to move all the data logic to services/actions/helpers

# Examples

## Testing a component (city-add.component.spec.ts)
```
const wrapper = shallowMount<any>(CityAddComponent, {
    localVue
});

await nextTick();

expect(wrapper.vm.testableMethods(2)).to.equal(3);
```

## Spying an injected service (city-list.component.spec.ts)
```
const spyCitiesServiceRemove = sinon.stub()
mockInject(wrapper.vm, 'citiesService', {
    remove: spyCitiesServiceRemove
})

await nextTick()
wrapper.vm.remove();

expect(spyCitiesServiceRemove).to.be.called;
spyCitiesServiceRemove.restore();
```

## Spying fetch (cities.service.spec.ts)
```
const route = `/api`
const spyFetchCitiesSearch = fetchStub(JSON.stringify(responseObject));

await citiesService.search();

expect(spyFetchCitiesSearch.withArgs(route)).to.be.called;
```
