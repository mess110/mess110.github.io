---
layout: post
title: email wildcards
---

All names are fictional and obfuscated to not reveal identities or entities. The
event is real.

So how do I even begin?

Meet Willy. Willy knows what email wildcards are.

```
john.doe@email.com
john.doe+provider@email.com
john.doe+whatever@email.com
```

When sending an email to any of the above addresses, `johndoe@gmail.com`
receives all of them. In theory, according to the email specifications
you can place a dot anywhere in the address and it is the same email
address. You can also add a + and write whatever you want after it
and still receive it. It can be used as a way to filter out spam,
mailing lists signup. A lot of use cases.

When I signup for a service I usually add +provider before the @
so I can know if I they sell my email address. I signed up for a
service which facilitates paying taxes. I use the email
`john.doe+provider_name@email.com`, where `provider_name` is
the service.

Years go by, I want to reset my password. I try to recover
my password but don't get the email to reset it.. I notice, the form
resets to `john.doeprovider_name@email.com`. After many
attempts it hits me. They don't support wildcards.

So what do I do? I create a new email. `john.doeprovider_name@email.com`,
reset the password and it arrives. I manage to reset my password
and change my email to `john.doe@email.com`.

Lesson? Use an email validator. And don't fuck with peoples taxes,
its ridiculous to have to create an email address which matches
what they wrongly stored in their database so one can actually use
the service.

It could have been way worse though. At least I could change my
email to remove the wildcard..


<br />
<br />
