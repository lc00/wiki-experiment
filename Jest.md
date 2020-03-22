```
beforeEach(() => {})

describe.only("behavior", () => {
  it("should do something", () => {
    expect().toBeTruthy()
  })
  it("should do something", done => {
    expect().toBeTruthy()
    done()
  })
})
```

## Flags

* `.not`
* `.resolves`

## Assertions

* `.toBe(referenceEquality)`
* `.toEqual(valueEquality)`
* `.toBeTruthy()` / `.toBeFalsy()`
* `.toBeNull()` / `.toBeDefined()`, / `.toBeUndefined()`
* `.toBeGreaterThan()`, `toBeGreaterThanOrEqual()`
* `.toBeCloseTo()` (fixes floating point math)
* `.toMatch(/regex/)`
* `.toContain()`
* `.anything()` / `.any(Type)`

## Mocks

* `const mockedFunction = jest.fn()`
* `const mockedFunction = jest.fn(someParameter => "some value")`
* `.toHaveBeenCalled`
* `.toHaveBeenCalledWith`
* `.mockReturnValue()` / `.mockReturnValueOnce()`
* `.mockResolvedValue()` / `.mockResolvedValueOnce()`
* `jest.mock("axios")`

## Timers

* `jest.useFakeTimers()`
* `jest.runAllTimers()`
* `jest.advanceTimersByTime(1000)`
