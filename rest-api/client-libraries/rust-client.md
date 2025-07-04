---
description: Our open source client is available under MIT and Apache 2.0 License.
---

# Rust Client

You can find the official ilert Rust client on our Github organization: [https://github.com/iLert/ilert-rust](https://github.com/iLert/ilert-rust)

Install as usual with cargo `ilert = "0.2.3"`

```rust
use ilert::ilert::ILert;
use ilert::ilert_builders::{UserApiResource, EventApiResource, ILertEventType};

let mut client = ILert::new().unwrap();
client.auth_via_token("your-api-token").unwrap();

let event_result = client
    .post()
    .event(
        "44c7afdc-0b3e-4344-b48a-5378a963231f",
        ILertEventType::ALERT,
        "Host srv/mail01 is CRITICAL",
        None,
        None)
    .execute()
    .unwrap();

let user_result = client
    .get()
    .users()
    .execute()
    .unwrap();
```

Please feel free to [reach out to us](../../contact.md) with a Github issue in case you need help or have feature requests.
