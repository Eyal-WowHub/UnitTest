# UnitTest

A library that offers an easy, efficient, and organized way to create, manage, and run unit tests.

To run the tests, create a macro and paste the following script: `/run LibStub("UnitTest-1.0"):Run()`.

### Example:

1. Calculator
```lua
-- Math.lua
local T = UnitTest_Table("Math", {
    Add = function(a, b)
        return a + b
    end,
    Divide = function(a, b)
        assert(b ~= 0, "Divided by zero. The denominator cannot be zero.")

        return a / b
     end
}, ...)

do
    local Add = T:Test("Add")

    Add["Should return 3"] = function(self, math)
        self:Assert(math.Add(1, 2) == 3)
    end
end

do
    local Divide = T:Test("Divide")

    Divide["Should throw when divided by zero"] = function(self, math)
        self:Capture(function()
            math.Divide(1, 0)
        end)
    end
end
```
2. UnitTest
```lua
-- Modules.lua
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
+ Calculator (Modules: 1)
-----------------------------------------------------------------------------------------------
    + Math (Scopes: 2)
        + Add (Tests: 1)
            + Should return 3
        + Divide (Tests: 1)
            + Should throw when divided by zero
    <Test Failure> The function should have thrown an error, but it did not.
    at 'Interface/AddOns/WowTestsDriver/Tests/MathTests.lua:24'
    in 'Interface/AddOns/WowTestsDriver/Tests/MathTests.lua:23'.
    Divided by zero. The denominator cannot be zero.
-----------------------------------------------------------------------------------------------
+ UnitTest (Modules: 1)
-----------------------------------------------------------------------------------------------
    + UnitTest-1.0 (Scopes: 1)
       + Modules (Tests: 1)
          + Create a module
-----------------------------------------------------------------------------------------------
Tests: 3 | Addons: 2 | Modules: 2 | Scopes: 3 | Passed: 2 | Failed: 1
-----------------------------------------------------------------------------------------------
```







