# Intellij Lerna Example

See stack overflow question [here](https://stackoverflow.com/questions/57561447/intellij-find-usages-doesnt-work-across-lerna-packages)

This is a lerna monorepo where "b-package" has a dependency on "a-package".  In IntelliJ, I am observing a bug (or probably a misconfiguration on my part), where "find usages" does not work across the lerna packages.

To reproduce:

1. Open this project in IntelliJ IDEA
2. `npm install`
3. `lerna bootstrap --hoist`
4. `lerna exec --ignore "root" -- "tsc -b"`
2. Navigate to `b-package/src/b.ts`
3. Attempt to "go to declaration" of the `aFn()` function.  Observe that it navigates you correctly to `a-package/src/a.ts`
4. Attempt to "find usages" of the `aFn()` function.  Notice that it returns zero results.  

Since the "go to declaration" works, I know Intellij is aware of the dependency in one direction, I just need to figure out how to make it aware in the other "find usages" direction.
