---
layout: episode
title: "Tools"
teaching: 10
exercises: 0
questions:
  - "What tools are out there?"
objectives:
  - "Discover the tool that fits your needs."
keypoints:
  - "Python and C/C++ have better tooling for automated tests and you can use those also for Fortran projects (via `iso_c_binding`)."
---

## Unit test frameworks

- Python
    - [pytest](http://doc.pytest.org)
    - [nose](http://nose.readthedocs.io)
    - [doctest](https://docs.python.org/2/library/doctest.html)
    - [unittest](https://docs.python.org/2/library/unittest.html)

- R
    - [testthat](https://github.com/hadley/testthat)

- C(++)
    - [Google Test](https://github.com/google/googletest)
    - [Catch2](http://catch-lib.net)
    - [cppunit](https://freedesktop.org/wiki/Software/cppunit/)
    - [Boost.Test](http://www.boost.org/doc/libs/1_62_0/libs/test/doc/html/index.html)
    - [UnitTest++](http://unittest-cpp.github.io)

- Fortran
    - [pFUnit](https://sourceforge.net/projects/pfunit/)
    - [FRUIT](https://sourceforge.net/projects/fortranxunit/)
    - [Ftunit](http://flibs.sourceforge.net/ftnunit.html)

---

## [pytest](http://doc.pytest.org)

Very easy to set up: Anaconda, Miniconda, or virtualenv.

Very easy to use: Prefix a function with "test\_" and the test runner will execute it.
No need to subclass anything.

```python
def get_word_lengths(s):
    """
    Returns a list of integers representing
    the word lengths in string s.
    """
    return [len(w) for w in s.split()]

def test_get_word_lengths():
    text = "Three tomatoes are walking down the street"
    assert get_word_lengths(text) == [5, 8, 3, 7, 4, 3, 6]
```

- [Example output](https://travis-ci.org/bast/pytest-demo/builds/104182942)
- [Example project](https://github.com/bast/pytest-demo)

---

## [Google Test](https://github.com/google/googletest)

- Widely used
- Very rich in functionality

```cpp
#include "gtest/gtest.h"
#include "example.h"

TEST(example, add)
{
    double res;
    res = add_numbers(1.0, 2.0);
    ASSERT_NEAR(res, 3.0, 1.0e-11);
}
```

- [Example output](https://travis-ci.org/bast/gtest-demo/builds/104190982)
- [Example project](https://github.com/bast/gtest-demo)

---

## [pFUnit](https://sourceforge.net/projects/pfunit/)

- Very rich in functionality
- Requires modern Fortran compilers (uses F2003 standard)

```fortran
@test
subroutine test_add_numbers()

   use hello
   use pfunit_mod

   implicit none

   real(8) :: res

   call add_numbers(1.0d0, 2.0d0, res)
   @assertEqual(res, 3.0d0)

end subroutine
```

- [Example output](https://travis-ci.org/bast/pfunit-demo/builds/104193675)
- [Example project](https://github.com/bast/pfunit-demo)

---

## Services to deploy testing and coverage

- [Travis CI](https://travis-ci.org)
- [GitLab CI](https://about.gitlab.com/features/gitlab-ci-cd/)
- [Coveralls](https://coveralls.io)
- [Codecov](https://codecov.io)
