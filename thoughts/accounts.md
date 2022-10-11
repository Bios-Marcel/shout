# Accounts

* Read-Only access to posts without requiring account
* Register via telephone number
  * Don't save telephone number on backend, hash before saving
    * Slow hashing algorithm to avoid rainbow table usage
  * Block certain telephone numbers (payphones and such)
  * Read-Only access even when banned (basically like not having an account)
