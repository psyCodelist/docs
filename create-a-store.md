# Create a store

Currently supported Kafka stores include:

* [Confluent Cloud](https://www.confluent.io/confluent-cloud/)
* [Amazon MSK](https://aws.amazon.com/msk/)

### Create a store <a href="#_create_a_store" id="_create_a_store"></a>

1.  From the left menu, click **Stores** and click on Plus button.



    <figure><img src=".gitbook/assets/Screenshot 2023-01-18 at 12.00.09 PM.png" alt=""><figcaption></figcaption></figure>
2. Select the **Store Type**
3.  Select the Amazon **Availability Zone**.

    |   | Only AWS **us-east-1** is supported at this time. |
    | - | ------------------------------------------------- |
4.  Enter a unique **Name**.

    |   | Store names are limitied to maximum of 255 characters. Only alpha characters, numbers, dashes, and underscores are allowed. |
    | - | --------------------------------------------------------------------------------------------------------------------------- |
5. Add one or more **URLs** of your Kafka brokers to connect to the store.
6.  (Optional) Complete the Authentication options as appropriate for your store.

    |   | If you are using Amazon MSK, there is no need for additional authentication. |
    | - | ---------------------------------------------------------------------------- |
7. Click **Create**.

### Authentication options <a href="#auth-options" id="auth-options"></a>

<figure><img src=".gitbook/assets/Screenshot 2023-01-18 at 12.06.43 PM (1).png" alt=""><figcaption></figcaption></figure>

| Disable SSL encryption                                                        | Toggle to enable or disable TLS/SSL encryption. Enabled by default.                                                                                    |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Server hostname verification                                                  | Verifies that the server certificate has a valid [SAN](https://www.snia.org/education/storage\_networking\_primer/san/what\_san). Selected by default. |
| TLS key                                                                       | Optional. Client certificate key for mutual TLS authentication.                                                                                        |
| TLS certificate                                                               | Optional. Client certificate for mutual TLS authentication.                                                                                            |
| [Certificate Authority](https://en.wikipedia.org/wiki/Certificate\_authority) | The CA entity that issued the certificate.                                                                                                             |
| SASL Hash Function                                                            | SASL hash function for user authentication. Available options: NONE (default), PLAIN, SHA256, SHA512                                                   |
| Username                                                                      | Username for SASL authentication.                                                                                                                      |
| Password                                                                      | Password for SASL authentication.                                                                                                                      |
