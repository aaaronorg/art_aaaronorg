task default: %w[Deploy_GHPs]

desc "Deploy to github pages"
task :Deploy_GHPs do
  puts "\n## Pull down latest master branch from github"
  status = system("git checkout -B master github/master")
  puts status ? "Success" : "Failed"
  puts "\n## rename master branch to old-master"
  status = system("git branch -m old-master")
  puts status ? "Success" : "Failed"
  puts "\n## switch back to source branch"
  status = system("git checkout source")
  puts status ? "Success" : "Failed"
  puts "\n## Change name of source branch to master tempororily"
  status = system("git branch -m master")
  puts status ? "Success" : "Failed"
  puts "\n## Mirror old source branch to temporary source branch"
  status = system("git checkout -b temp-source")
  puts status ? "Success" : "Failed"
  puts "\n## Switch to  master branch"
  status = system("git checkout master")
  puts status ? "Success" : "Failed"
  puts "\n## Forcing the _site subdirectory to be project root"
  status = system("git filter-branch --subdirectory-filter _site/ -f")
  puts status ? "Success" : "Failed"
  puts "\n## Push updated master branch back over to github"
  status = system("git push github master -f")
  puts status ? "Success" : "Failed"
  puts "\n## Switch to temp-source branch"
  status = system("git checkout temp-source")
  puts status ? "Success" : "Failed"
  puts "\n## Rename branch back to source"
  status = system("git branch -m source")
  puts status ? "Success" : "Failed"
  puts "\n## Switch to old- master branch"
  status = system("git checkout old-master")
  puts status ? "Success" : "Failed"
  puts "\n## Deleting master branch"
  status = system("git branch -D master")
  puts status ? "Success" : "Failed"
  puts "\n## Rename old-master branch back to master"
  status = system("git branch -m master")
  puts status ? "Success" : "Failed"
  puts "\n## Fetch all"
  status = system("git fetch --all")
  puts status ? "Success" : "Failed"
  puts "\n## Reset github/master"
  status = system("git reset --hard github/master")
  puts status ? "Success" : "Failed"
  puts "\n## Push all"
  status = system("git push --all")
  puts status ? "Success" : "Failed"
  puts "\n## Switch back to source branch"
  status = system("git checkout source")
  puts status ? "Success" : "Failed"
end
