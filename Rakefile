##
## Rakefile for Building Report from Rakefile
##
require 'rake/clean'

MD_FILES = FileList["*.md"].exclude("README.md")
TEX_FILES = MD_FILES.ext(".tex")

CLEAN.include(TEX_FILES)

task :default => [:tex2pdf] do
  
end
  
task :tex2pdf => [:md2tex] do
  
end

task :md2tex => TEX_FILES

# *.md -> *.tex 変換ルール
rule ".tex" => ".md" do |t|
  sh "pandoc", "-o", t.name, t.source
end
