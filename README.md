## Insights on installing oh-my-zsh and Ruby on Macs with Apple Silicon (M1).
  
  Installing Oh-My-Zsh, Ruby and Rails on my personal Macbook M1 lead to some substantial problems- My Ruby version was set to Apple's default one and, hence, rails was considered as being uninstalled. In this article, you'll find a quick overview of the problem, how I solved it and where I believe the problem might reside.
  
### Initial Config
  As you see (through the timestamp on top), my Mac is currently running with rbenv's version of Ruby 2.7 and I am on Rails 6.1.
  <img width="762" alt="Screenshot 2021-11-30 at 14 33 18" src="https://user-images.githubusercontent.com/88334281/144034905-6236f6ad-4b29-475a-a74f-1bab34116d89.png">

### Problem
  As soon as I install Oh-My-Zsh with the command `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`, I encounter this problem. My Ruby version is set to Apple's default of 2.6 and Rails seem to be absent (I did not manually remove the rails gem or anything).
  <img width="762" alt="Screenshot 2021-11-30 at 14 34 18" src="https://user-images.githubusercontent.com/88334281/144035187-d0e2f91c-82bc-44f2-b0dc-afa148b3dd08.png">

### Proposed solution
  To resolve my issue, I uninstalled Oh-My-Zsh with `uninstall_oh_my_zsh`. As you see, as soon as it is uninstalled, my Ruby version is set back to that of rbenv and Rails mysteriously appears...
  
  <img width="762" alt="Screenshot 2021-11-30 at 14 37 01" src="https://user-images.githubusercontent.com/88334281/144035398-315d8630-134b-4499-ac95-ad3695c4de59.png">

  <img width="762" alt="Screenshot 2021-11-30 at 14 37 46" src="https://user-images.githubusercontent.com/88334281/144035429-65fad40c-59d5-476d-8439-6548cff870eb.png">

### Probable cause of the problem

  This seemed quite odd at the beginning until I opened the .zshr file in my root. Prior to installing Oh-My-Zsh, I had the two following lines in that file.
<img width="1136" alt="Screenshot 2021-11-30 at 14 38 04" src="https://user-images.githubusercontent.com/88334281/144035574-1909a021-eafb-4e13-9c20-9837519ad407.png">

After I've installed Oh-My-Zsh, these two lines are removed from .zshr and this line pops into place

<img width="1136" alt="Screenshot 2021-11-30 at 14 36 15" src="https://user-images.githubusercontent.com/88334281/144035701-8682a7d5-5f73-4d73-82d4-7dfa38831fe9.png">

Naturally, having uninstalled Oh-My-Zsh, the two rbenv path lines in .zshr are back into place and the oh-my-zsh path is removed.

