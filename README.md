# UnitTest

A library that offers an easy, efficient, and organized way to create, manage, and run unit tests.

To run the tests, create a macro and paste the following script: `/run LibStub("UnitTest-1.0"):Run()`.

### Example:

```lua
-- DemoTests.lua
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

### Outputs:

```
-----------------------------------------------------------------------------------------------
+ WowTestsDriver (Modules: 1)
-----------------------------------------------------------------------------------------------
    + DemoTests (Scopes: 1)
       + DemoFunc (Tests: 1)
-----------------------------------------------------------------------------------------------
Tests: 1 | Addons: 1 | Modules: 1 | Scopes: 1 | Passed: 1 | Failed: 0
-----------------------------------------------------------------------------------------------
```







