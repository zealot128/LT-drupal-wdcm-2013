
require "fileutils"

desc "Refresh 3rd party assets"
task :copy_assets do
  sh "git submodule init && git submodule update"

end


desc "Deploy to github pages"
task :deploy do
    sh "git diff-index --quiet HEAD --" do |ok,res|
      if !ok
        $stderr.puts "You have uncommitted changes!"
        sh "git status --short"
        exit 1
      end
    end
  sh "middleman build"
  sh "git checkout -B gh-pages"
  mv "build/*" "."
  sh "git add ."
  sh "git status --short"
  puts "Commit changes and push:\ngit push origin gh-pages"
end
