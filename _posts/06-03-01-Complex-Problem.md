---
title: Complex Problem
isChild: true
anchor: complex_problem
---

## Karmaşık Problemler {#complex_problem_title}

Eğer daha önce Dependency Injection hakkında okuduysanız, *"Inversion of Control" (Kontrolün Ters Çevirilmesi)* ya da *"Dependency Inversion Principle" (Bağımlılığın Ters Çevirilmesi İlkesi)* kavramlarını duymuş olmalısınız.
Bunlar Dependency Injection ile çözülmeye çalışılan sorunlardır.

### Inversion of Control

“Kontrolün Tersine Çevirilmesi” kelime anlamında olduğu gibi, yapısal kontrolü nesnelerimizden tamamen ayrı tutarak sistemin kontrolünü tersine çevirmektir.
Dependency Injection açısından bakarsak, bu başka bir yerde yöneterek ya da oluşturarak bağımlılıkların bitirilmesi anlamına gelir.

For years, PHP frameworks have been achieving Inversion of Control, however, the question became, which part of control
are you inverting, and where to? For example, MVC frameworks would generally provide a super object or base controller that other
controllers must extend to gain access to its dependencies. This **is** Inversion of Control, however, instead of loosening
dependencies, this method simply moved them.

Dependency Injection allows us to more elegantly solve this problem by only injecting the dependencies we need, when we need them,
without the need for any hard coded dependencies at all.

### Dependency Inversion Principle

Dependency Inversion Principle is the "D" in the S.O.L.I.D set of object oriented design principles that states one should
*"Depend on Abstractions. Do not depend on concretions."*. Put simply, this means our dependencies should be interfaces/contracts or abstract
classes rather than concrete implementations. We can easily refactor the above example to follow this principle.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(AdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
}

interface AdapterInterface {}

class MysqlAdapter implements AdapterInterface {}
{% endhighlight %}

There are several benefits to the `Database` class now depending on an interface rather than a concretion.

Consider that you are working in a team and the adapter is being worked on by a colleague. In our first example, we would have
to wait for said colleague to finish the adapter before we could properly mock it for our unit tests. Now that the dependency
is an interface/contract we can happily mock that interface knowing that our colleague will build the adapter based on that contract.

An even bigger benefit to this method is that our code is now much more scalable. If a year down the line we decide that we
want to migrate to a different type of database, we can write an adapter that implements the original interface and inject that instead,
no more refactoring would be required as we can ensure that the adapter follows the contract set by the interface.
