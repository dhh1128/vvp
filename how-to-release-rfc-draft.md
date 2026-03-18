# How to Release RFC Draft

1. Make sure that the last draft is tagged in the repo. If the final step in these instructions was neglected last time you did a release, you need to figure out the commit associated with that release, and tag it now.

2. Get a commit that is cleanly accepted after push.

3. `$ make next`

4. [Submit the .xml file](https://datatracker.ietf.org/submit/) that was produced in the versioned folder (NOT the .txt file).

5. Tag the repository so the next run of `make next` will increment the version. The tag you should use is the full draft name including a revision number. Something like this:

    `$ git tag -a draft-hardman-verifiable-voice-07`<br>
    `$ git push origin draft-ietf-unicorn-protocol-07`