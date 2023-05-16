The privkey.pem is generated with `openssl genrsa -aes128 -passout pass:foobar -out privkey.pem 3072`

and base64 encoded with `base64 -i privkey.pem > privkey.pem.base64`

It will be decoded with `base64 -i --decode privkey.pem.base64 > privkey.pem` in CI.

We put the privkey.pem.base64 to the github secrets

During the CI process the pass will be asked.
https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch/

If the pass is `foobar` the process will be finished succesfully.

`openssl rsa -in privkey.pem -passin pass:foobar -pubout -out privkey.pub`