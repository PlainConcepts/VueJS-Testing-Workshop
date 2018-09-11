# Unit testing with vue

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