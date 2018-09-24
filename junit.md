# JUnit

## Setting up JUnit
1. Create new project
2. `option enter brings up menu`
3. Create a new folder outside of `src` - right-click project, `new` > `new directory` > `test`
4. Go to `Project Structure` > `Modules` > select `test` folder and mark with `tests` flag
5. `option enter` keys on class name to generate test file
6. Select `junit 5` for testing library
7. To run test, `control option R`.

## Assertions
| Assertion | Description |
| --- | --- |
`assertEquals(expected, actual);` | checks that two primitives/objects are equal
`assertFalse(boolean);` | checks that condition is false
`assertTrue(boolean);` | checks that condition is true
`assertNotNull(object);` | checks that an object isn't null
`assertNull(object);` | checks that an object is null
`assertSame(object1, object2);` | checks if two object references point to the same object
`assertNotSame(object1, object2);` | checks if two object references do not point to the same object
`assertArrayEquals(expected, actual);` | checks whether two arrays are equal to each other

## Annotations
| Annotation | Description |
| --- | --- |
`@Test` | Annotated method can be run as a test case
`@Before` | Annotated method will be run prior to each test method
`@After` | Annotated method will be run after each test method
`@BeforeClass` | Annotated method will be run once before any test
`@AfterClass` | Annotated method will run after all tests have finished
`@Ignore` | Annotated test will be ignored and not executed