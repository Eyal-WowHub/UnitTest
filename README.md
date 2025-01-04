# UnitTest

A library that offers an easy, efficient, and organized way to create, manage, and run unit tests.

To run the tests, create a macro and paste the following script: `/run LibStub("UnitTest-1.0"):Run()`.

### Examples:

```lua
-- DemoTest: Demo.lua
local T = UnitTest_Table("DemoTests", {
    DemoFunc = function()
    end
}, ...)

do
    local DemoFunc = T:Test("DemoFunc")

    DemoFunc["Should fail first"] = function(self, ref)
        self:Assert(false)
    end
end
```
```lua
-- UnitTest: Modules.lua
local T = UnitTest_Library("UnitTest-1.0", ...)

do
    local Modules = T:Test("Modules")

    Modules["Create a module"] = function(self, ref)
        self:Assert(Modules ~= nil)
    end
end
```

### Outputs:

```
-----------------------------------------------------------------------------------------------
+ WowTestsDriver (Modules: 1)
-----------------------------------------------------------------------------------------------
    + DemoTest (Scopes: 1)
       + DemoFunc (Tests: 1)
          + Should fail first
    ...ace/AddOns/WowTestsDriver/Libs/UnitTest/UnitTest.lua:24: Assertion failed: The test condition should have been true, but it was false.
-----------------------------------------------------------------------------------------------
+ UnitTest (Modules: 1)
-----------------------------------------------------------------------------------------------
    + UnitTest-1.0 (Scopes: 1)
       + Modules (Tests: 1)
          + Create a module
-----------------------------------------------------------------------------------------------
Tests: 2 | Addons: 2 | Modules: 2 | Scopes: 2 | Passed: 1 | Failed: 1
-----------------------------------------------------------------------------------------------
```







