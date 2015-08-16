# Maintainer: M0Rf30 <morfeo89 [at] hotmail [dot] it>
# Contributor: Eric Engestrom <aur [at] engestrom [dot] ch>

pkgname=leap-motion-sdk-beta
_major=2.0.3
_build=17004
pkgver=${_major}.${_build}
pkgrel=1
pkgdesc="The Leap Motion Developer SDK"
arch=('i686' 'x86_64')
url="https://developer.leapmotion.com/downloads"
depends=('leap-motion-driver-beta')
conflicts=('leap' 'leap-motion-sdk')
license=('custom')
source=("https://dl.dropboxusercontent.com/u/7226803/LeapDeveloperKit_${_major}%2B${_build}_linux.tgz"
	 LICENSE)

package() {
  cd ${srcdir}/LeapDeveloperKit_${_major}+${_build}_linux/

  # copy docs
  mkdir -p ${pkgdir}/usr/share/doc/${pkgname}/
  cp -r LeapSDK/docs/* ${pkgdir}/usr/share/doc/${pkgname}/

  # copy samples, util
  cp -r LeapSDK/{samples,util} ${pkgdir}/usr/share/doc/${pkgname}/

  # copy includes
  mkdir -p ${pkgdir}/usr/include/
  cp -r LeapSDK/include/* ${pkgdir}/usr/include/

  # copy libs
  mkdir -p ${pkgdir}/usr/lib/Leap

  cp LeapSDK/lib/{LeapJava.jar,Leap.py} ${pkgdir}/usr/lib/Leap

  if [ "$CARCH" == 'x86_64' ]; then
    cp LeapSDK/lib/x64/{LeapPython,libLeapCSharp,libLeapJava}.so ${pkgdir}/usr/lib/Leap
  else
    cp LeapSDK/lib/x86/{LeapPython,libLeapCSharp,libLeapJava}.so ${pkgdir}/usr/lib/Leap
  fi
  cp LeapSDK/lib/LeapCSharp.NET{3.5,4.0}.dll ${pkgdir}/usr/lib/Leap

  # copy examples
#  mkdir -p ${pkgdir}/usr/share/doc/${pkgname}/examples
#  cp -r Examples/* ${pkgdir}/usr/share/doc/${pkgname}/examples/

  # Copy license
  install -D -m644 "${srcdir}"/LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

md5sums=('c6c87427b98720707c736070dba68f80'
         '78a4f0934b105397d1f7b17d06e4717c')
