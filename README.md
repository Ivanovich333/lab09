```
❯ export GITHUB_TOKEN=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
❯ export GITHUB_USERNAME=Ivanovich333
```
```
❯ git clone git@github.com:Ivanovich333/lab08.git projects/lab09
Cloning into 'projects/lab09'...
remote: Enumerating objects: 48, done.
remote: Counting objects: 100% (48/48), done.
remote: Compressing objects: 100% (26/26), done.
remote: Total 48 (delta 10), reused 48 (delta 10), pack-reused 0
Receiving objects: 100% (48/48), 13.61 KiB | 3.40 MiB/s, done.
Resolving deltas: 100% (10/10), done.
```
```
❯ cd projects/lab09
❯ git remote remove origin
❯ git remote add origin git@github.com:Ivanovich333/lab09.git
```
```
❯ alias gsed=sed
❯ alias pbcopy='xclip -selection clipboard'
❯ alias pbpaste='xclip -selection clipboard -o'
❯ export GPG_PACKAGE_NAME=gpg
```
```
❯ gpg --list-secret-keys --keyid-format LONG
gpg: directory '/home/ivanovich333/.gnupg' created
gpg: /home/ivanovich333/.gnupg/trustdb.gpg: trustdb created
```
```
❯ gpg --full-generate-key
```
```
❯ gpg --list-secret-keys --keyid-format LONG
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2024-05-25
[keyboxd]
---------
sec   rsa3072/00AAE7D7EA81263A 2024-05-25 [SC]
      72F4D3771EE9BFF9EB3005C000AAE7D7EA81263A
uid               [  абсолютно ] Yarik (dwe) <vizgalovyaroslav@gmail.com>
ssb   rsa3072/484C340C06624F22 2024-05-25 [E]
```
```
❯ gpg -K Yarik

sec   rsa3072 2024-05-25 [SC]
      72F4D3771EE9BFF9EB3005C000AAE7D7EA81263A
uid         [  абсолютно ] Yarik (dwe) <vizgalovyaroslav@gmail.com>
ssb   rsa3072 2024-05-25 [E]
```
```
❯ GPG_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep ssb | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
❯ echo ${GPG_KEY_ID}
46ED3BD2EBBF604B
❯ GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
❯ echo ${GPG_SEC_KEY_ID}
57B709282F8BC979
❯ gpg --armor --export ${GPG_KEY_ID} | pbcopy
```
```
❯ test -r ~/.bash_profile && echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile
❯ echo 'export GPG_TTY=$(tty)' >> ~/.profile
```
```
❯ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"

-- The C compiler identification is GNU 14.1.1
-- The CXX compiler identification is GNU 14.1.1
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/gcc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/Ivanovich333/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: bfeb507 | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/Ivanovich333/.hunter/_Base/a20151e/bfeb507/4abab25/Install (ver.: 1.14.0)
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done (1.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/Ivanovich333/VS/TIMP/Ivanovich333/workspace/projects/lab09/_build
❯ cmake --build _build --target package
[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/Ivanovich333/VS/TIMP/Ivanovich333/workspace/projects/lab09/_build/print-.1.0.0-Linux.tar.gz generated.
```
```
❯ git tag -s v0.1.0.0 -m "tag for TIMP"
❯ git tag -v v0.1.0.0

object a64b0fe363f3700fac71c3f64fa89dc1f6b9f48d
type commit
tag v0.1.0.0
tagger Ivanovich333 <vizgalovyaroslav@gmail.com> 1715590098 +0300

tag for TIMP
gpg: Signature made Mon 25 May 2024 11:48:18 AM MSK
gpg:                using EDDSA key 57ED3FA81017197F605026EC57B709282F8BC979
gpg: Good signature from "Ivanovich333 (gpg key for TIMP) <vizgalovyaroslav@gmail.com>" [ultimate]
```
```
❯ git show v0.1.0.0
```
```
❯ git push origin main --tags
Enumerating objects: 49, done.
Counting objects: 100% (49/49), done.
Delta compression using up to 8 threads
Compressing objects: 100% (27/27), done.
Writing objects: 100% (49/49), 13.90 KiB | 13.90 MiB/s, done.
Total 49 (delta 10), reused 48 (delta 10), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (10/10), done.
To github.com:Ivanovich333/lab09.git
 * [new branch]      main -> main
 * [new tag]         v0.1.0.0 -> v0.1.0.0
```
```
❯ github-release --version
github-release v0.9.0
```
```
❯ github-release info -u Ivanovich333 -r lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/Ivanovich333/lab09/commits/a64b0fe363f3700fac71c3f64fa89dc1f6b9f48d)
releases:
```
```
❯ github-release release \
--user Ivanovich333 \
--repo lab09 \
--tag v0.1.0.0 \
--name "libprint" \
--description "release"
```
```
❯ github-release info -u ${GITHUB_USERNAME} -r lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/Ivanovich333/lab09/commits/a64b0fe363f3700fac71c3f64fa89dc1f6b9f48d)
releases:
- v0.1.0.0, name: 'libprint', description: 'release', id: 155484467, tagged: 25/05/2024 at 08:48, published: 25/05/2024 at 11:16, draft: ✗, prerelease: ✗
  - artifact: print-Linux-x86_64.tar.gz, downloads: 0, state: uploaded, type: application/octet-stream, size: 5.7 kB, id: 167617837
```
```
❯ wget https://github.com/${GITHUB_USERNAME}/lab09/releases/download/v0.1.0.0/${PACKAGE_FILENAME}
--2024-05-25 14:21:01--  https://github.com/Ivanovich333/lab09/releases/download/v0.1.0.0/print-Linux-x86_64.tar.gz
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'
Resolving github.com (github.com)... 140.82.121.4
Connecting to github.com (github.com)|140.82.121.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/799827584/28715b80-f439-4aaa-9a00-338f8994309e?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240525%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240525T112101Z&X-Amz-Expires=300&X-Amz-Signature=f3af82b6764716b434579dac3112f19a31f21bf7538214728d277ffe3515a65a&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=799827584&response-content-disposition=attachment%3B%20filename%3Dprint-Linux-x86_64.tar.gz&response-content-type=application%2Foctet-stream [following]
--2024-05-25 14:21:02--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/799827584/28715b80-f439-4aaa-9a00-338f8994309e?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240525%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240525T112101Z&X-Amz-Expires=300&X-Amz-Signature=f3af82b6764716b434579dac3112f19a31f21bf7538214728d277ffe3515a65a&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=799827584&response-content-disposition=attachment%3B%20filename%3Dprint-Linux-x86_64.tar.gz&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.108.133, 185.199.110.133, 185.199.109.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5675 (5.5K) [application/octet-stream]
Saving to: ‘print-Linux-x86_64.tar.gz’

print-Linux-x86_64.tar.gz   100%[=========================================>]   5.54K  --.-KB/s    in 0s

2024-05-25 14:21:02 (15.6 MB/s) - ‘print-Linux-x86_64.tar.gz’ saved [5675/5675]
```
```
❯ tar -ztf ${PACKAGE_FILENAME}
print-.1.0.0-Linux/lib/
print-.1.0.0-Linux/lib/libprint.a
print-.1.0.0-Linux/include/
print-.1.0.0-Linux/include/print.hpp
print-.1.0.0-Linux/cmake/
print-.1.0.0-Linux/cmake/print-config.cmake
print-.1.0.0-Linux/cmake/print-config-noconfig.cmake
print-.1.0.0-Linux/bin/
print-.1.0.0-Linux/bin/demo
```
