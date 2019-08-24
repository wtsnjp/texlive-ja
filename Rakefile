# Rakefile for wtsnjp/texlive-ja
require 'rake/clean'
require 'pathname'

# basics
PKG_NAME = "texlive-ja"

# woking/temporaly dirs
PWD = Pathname.pwd
TMP_DIR = PWD + "tmp"

# cleaning
CLEAN.include([
  "*.aux", "*.dvi", "*.log", "*.synctex.gz", "*.toc", "*.out", "tmp"
])
CLOBBER.include(["*.pdf", "*.zip"])

# deault
task default: :archive

desc "Build the document without the tombow"
task :build do
  # initialize the build
  BUILD_DIR = TMP_DIR + "build"
  rm_rf BUILD_DIR
  mkdir_p BUILD_DIR

  # generate the main source (without the tombow option)
  MAIN_TEX = BUILD_DIR + "#{PKG_NAME}.tex"
  sh "sed s/,tombow// #{PKG_NAME}.tex > #{MAIN_TEX}"

  # build the document
  cd BUILD_DIR
  sh "TEXINPUTS='#{BUILD_DIR}:#{PWD}//:' llmk #{PKG_NAME}.tex"
end

desc "Create an archive for TeX Live"
task :archive => :build do
  # initialize the target
  TARGET_DIR = TMP_DIR + PKG_NAME
  rm_rf TARGET_DIR
  mkdir_p TARGET_DIR

  # copy supplementary files
  cd PWD
  pkg_contents = ["README.md", "img", "#{PKG_NAME}.sty"]
  cp_r pkg_contents, TARGET_DIR

  # copy the main document from the build dir
  cd BUILD_DIR
  cp ["#{PKG_NAME}.tex", "#{PKG_NAME}.pdf"], TARGET_DIR

  # create zip archive
  cd TMP_DIR
  sh "zip -q -r #{PKG_NAME}.zip #{PKG_NAME}"
  mv "#{PKG_NAME}.zip", PWD
end
